+++
title = "Website hosting, worldwide CDN and DDoS protection, all for free!"
date = 2025-07-03
slug = "website-hosting-worldwide-cdn-and-ddos-protection-all-for-free"
path = "/2025/07/03/website-hosting-worldwide-cdn-and-ddos-protection-all-for-free/"

[taxonomies]
categories = ["Meta"]
tags = ["CDN", "ChatGPT", "Cloudflare", "CodeReflections", "DDoS Protection",
"Free", "GitHub Pages", "Static Website", "Website Hosting"]
+++

When I created this blog website, I decided from the start to use a static site
generator instead of a dynamic site like Wordpress, so that the site would be
faster and also suitable for free hosting on [GitHub
Pages](https://pages.github.com/), rather than having to pay a hosting provider
to host the website.  Now I've leveled up, moving
[CodeReflections.com](https://codereflections.com/) to
[Cloudflare](https://cloudflare.com/), utilizing their awesome CDN (Content
Delivery Network) to cache the website worldwide with excellent protection
against DDoS (Distributed Denial of Service) attacks — also for free!

<!-- more -->

Naturally, I had assumed all along that using a high-quality CDN like
Cloudflare would require paying a monthly charge.  Given that this blog is
still just getting started, I didn't see any point in paying for CDN services
or DDoS protection until such time as there is sufficient traffic to warrant
it.  I don't expect that to happen in the foreseeable future.  (Granted, there
is the hypothetical possibility of making a blog post that somehow goes viral,
but that seems unlikely and certainly isn't foreseeable!)

However, the other day I was asking ChatGPT (4o) for ideas of how I might be
able to get any visitor logs or implement a page view counter for the site
while hosting it on GitHub pages.  It said that GitHub only offers basic
information about how many times the repository has been viewed, without any
per-URL breakdown.  However, one of the suggestions it offered was to put
Cloudflare in front of the domain, which would allow me to use their Web
Analytics to get more detailed information.

I was surprised to learn that Cloudflare had a free plan that I could use for
the site.  I hadn't expected anyone to offer free CDN services, and I hadn't
researched CDN options since I saw no imminent need to use them.  However,
having a CDN is certainly a "nice to have" option!  If I could use Cloudflare
for free, that seemed like a no-brainer.

Moving the DNS hosting to Cloudflare appears to be a prerequisite for using the
Cloudflare CDN on the free plan, but I figured it was worth the trouble.
(Apparently I could avoid moving the DNS hosting by using a paid plan, but that
would defeat the purpose!)  So I ended up moving the DNS hosting for
[codereflections.com](https://codereflections.com/) to Cloudflare, then I
updated the DNS entries to activate the Cloudflare reverse proxy servers to
cache the site, making it available worldwide on the Cloudflare CDN with
built-in DDoS protection! 🎉

Of course, I had to jump through some hoops and deal with some hassles along
the way, such as dealing with cached DNS information.  That much I expected,
but a more annoying example was when everything finally appeared to be correct
in the Cloudflare setup, and HTTPS was working for Firefox, but Google Chrome
kept reporting that the connection was "insecure".  It turned out that this was
happening solely because I had allowed Chrome to visit the site earlier, when I
was testing the basic pages and the HTTPS certificate wasn't ready yet.  Even
though the website was now returning a valid HTTPS certificate, Chrome just
kept insisting that the connection was "insecure" just because it remembered
the previous override with the invalid certificate! 🙄

Ultimately, I was forced to exit Chrome completely and restart it, after which
it forgot about the previous override and **finally** started reporting the
HTTPS connection as being secure.  (It's dumbfounding that Chrome's behavior is
so stupid in this respect!)

Once the website hosting on the Cloudflare CDN was working correctly, I spent a
couple hours going back and forth with ChatGPT about what caching rules I
should use for Cloudflare.  In the process, I had to research details to
confirm how the caching rules **actually** work, because ChatGPT gave me wrong
information several times and I had to correct it.  Based on our discussion and
the details about the website file structure that I provided, ChatGPT
recommended a total of 5 caching rules, which I ultimately refactored into 2
final rules.

We originally tried to use regular expressions in the rules, only to discover
that the free plan **disables** the regex matching feature in the rules engine.
Using it requires a paid business plan instead!

Here's the final caching rules I settled on:

<img src="/images/20250703_Cloudflare_Cache_Rules.png">

The first rule is based on a file extension preset that Cloudflare offers, and
identifies file types that can typically be cached for a long time.  ChatGPT
suggested setting this to 30 days, but I decided to limit the caching to 1 day
instead, just in case.  Here is the exact filter expression that this rule is
using; note that this list **doesn't** include `"htm"`, `"html"` or `"xml"`
file extensions:

```
(http.request.uri.path.extension in {"7z" "avi" "avif" "apk" "bin" "bmp" "bz2" "class" "css" "csv" "doc" "docx" "dmg" "ejs" "eot" "eps" "exe" "flac" "gif" "gz" "ico" "iso" "jar" "jpg" "jpeg" "js" "mid" "midi" "mkv" "mp3" "mp4" "ogg" "otf" "pdf" "pict" "pls" "png" "ppt" "pptx" "ps" "rar" "svg" "svgz" "swf" "tar" "tif" "tiff" "ttf" "webm" "webp" "woff" "woff2" "xls" "xlsx" "zip" "zst"})
```

Here's where it gets a little tricky.  The first cache rule has the following
Edge TTL configuration:

<img src="/images/20250703_Cloudflare_Rule1_Edge_TTL.png">

The idea behind the "Status Code TTL" entries is to ensure that "not found"
errors are only cached for 30 seconds instead of 1 day.  This is used for HTTP
status codes 404 and 410.  (Press the "Add status code setting" button twice to
enter both codes.)

Note that "30 seconds" **doesn't** appear in the default dropdown list, and
it's not obvious how to enter a non-default value: click inside the text input
area and type the number of **seconds** you want (e.g. 3600 for one hour or
86400 for one day), then select the new dropdown menu entry which appears
(matching the number of seconds you entered).

The second rule applies to HTML pages, the site search index and XML files for
Atom/RSS feeds; here is the filter expression:

```
(ends_with(http.request.uri.path, "/")) or (ends_with(http.request.uri.path, "search_index.en.js")) or (http.request.uri.path.extension in {"htm" "html" "xml"})
```

For the "Cache eligibility" setting, this rule uses "Eligible for cache",
contrary to ChatGPT's recommendation of using "Bypass cache" for HTML pages.
This allows cached copies to be stored on Cloudflare's edge servers, while
"Bypass cache" would always require the origin server to serve these requests.

The Edge TTL configuration for the second cache rule is more complicated than
the first rule:

<img src="/images/20250703_Cloudflare_Rule2_Edge_TTL.png">

In addition to the same "Status Code TTL" entries as above for "not found"
errors, this cache rule has additional entries for "found" status codes (200,
206 and 301), which are set to "No cache".  This still allows a cached copy to
be stored on Cloudflare's edge servers, but they must re-validate the request
each time with the origin server (GitHub Pages).

This guarantees that the response to these HTTP requests is always current,
using a conditional request to the origin server with the `If-Modified-Since`
header, which allows the origin server to send a short response in the case
that the file hasn't changed.  In practice, this will almost always be the
case.  This is much better than "Bypass cache", which wouldn't store a cached
copy at all, requiring the origin server to return the full response every
time, which is less efficient.

The second cache rule also configures Browser TTL to the "Bypass cache"
setting, to bypass the cache in the user's browser:

<img src="/images/20250703_Cloudflare_Rule2_Browser_TTL.png">

These cache rules should work well for this static site, while always staying
current with any content changes.

Next, I need to figure out Cloudflare's Web Analytics! 🤔
