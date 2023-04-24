+++
title = "Choosing a comment system."
date = 2023-04-23
slug = "choosing-a-comment-system"
path = "/2023/04/23/choosing-a-comment-system/"

[taxonomies]
categories = ["Meta"]
tags = ["ChatGPT", "CodeReflections", "Zola", "Remark42"]
+++

My lengthy conversation with ChatGPT continues!  In [yesterday's
post](/2023/04/22/choosing-a-blogging-platform), I decided to use Zola as the
blogging platform.  Now I have to figure out how to integrate a comment system
into a static site generator...

<!-- more -->

{{ first_msg() }}

I think I'll try using Zola.  What are the best privacy-oriented options to
integrate comment support into a Zola site, keeping all data locally?

{{ chatgpt_msg() }}

For a Zola site, you can consider using privacy-oriented, self-hosted
commenting systems that allow you to keep data under your control. Some options
to consider are:

1. Remark42: A lightweight, self-hosted commenting system with Markdown support
   and without any tracking features. It's easy to embed into your Zola site
and keeps data on your server.

2. Isso: A self-hosted commenting system that is also lightweight and simple to
   integrate into a Zola site. It doesn't use third-party trackers and stores
data on your server.

3. Commento: A self-hosted, privacy-focused commenting system that is easy to
   integrate and manage. It doesn't include any trackers, and you can control
the data storage.

These commenting systems can be installed on your server, and then you can
embed them into your Zola site. Remember that you'll need to have a server to
host these systems, as they require server-side components to store and manage
the comments.

{{ last_msg() }}

Did ChatGPT forget already?

{{ first_msg() }}

As we already discussed, I already signed up for the KVM VPS with
BuyVM/FranTech, so I'll have a place to host it.

{{ chatgpt_msg() }}

That's great! With your KVM VPS from BuyVM/FranTech, you have the necessary
resources to host a self-hosted commenting system. You can choose one of the
privacy-oriented options I mentioned earlier (Remark42, Isso, or Commento) and
set it up on your VPS.

To get started, you will need to:

1. Install the required dependencies for your chosen commenting system (usually
   documented in the project's README or installation guide).

2. Configure the commenting system according to your preferences and the
   requirements of your Zola site.

3. Integrate the commenting system into your Zola site by adding the necessary
   code snippets to your templates or content files.

Once you have set up the commenting system on your VPS and integrated it with
your Zola site, you'll be able to manage and store comments locally while
maintaining your users' privacy.

{{ user_msg() }}

How do Remark42, Isso and Commento compare with each other?

{{ chatgpt_msg() }}

Remark42, Isso, and Commento are all self-hosted, privacy-focused commenting
systems. Each of them has its own set of features and differences that you may
want to consider when choosing the best option for your website.

<ol>
<li>Remark42:

<ul>
<li>Written in Go.
<li>Supports social login (Google, Facebook, GitHub, etc.) and anonymous
commenting.
<li>Can import and export comments.
<li>Offers moderation tools, like editing, deleting, and pinning comments.
<li>Provides an upvote/downvote system and comment sorting options.
<li>Can be used as a replacement for Disqus.
</ul>

<li>Isso:

<ul>
<li>Written in Python.
<li>Supports anonymous commenting only (no social login).
<li>Offers moderation tools, like deleting comments.
<li>Provides an upvote/downvote system and comment sorting options.
<li>Can import and export comments.
<li>Lightweight and easy to set up.
</ul>

<li>Commento:

<ul>
<li>Written in Go.
<li>Supports social login (Google, Twitter, GitHub, etc.) and anonymous
commenting.
<li>Offers moderation tools, like editing, deleting, and approving comments.
<li>Provides an upvote/downvote system and comment sorting options.
<li>Can import and export comments.
<li>Has a clean and modern user interface.
</ul>
</ol>

All three options are privacy-focused and store the data locally, but they
differ in features and implementation. Your choice will depend on your
preferences, such as ease of setup, the availability of social logins, and the
user interface. Additionally, consider the programming language and potential
compatibility with your VPS setup.

{{ last_msg() }}

Okay, I can eliminate Isso.  I'll take Go over Python here, and social login is
a good idea.  Still, I'd rather have everything in Rust if I can.

{{ first_msg() }}

Are there any good comment solutions implemented in Rust?

{{ chatgpt_msg() }}

While there aren't as many Rust-based commenting systems as there are in other
languages, there are a few options you can consider:

1. Cactus Comments: Cactus Comments is a federated, self-hosted commenting
   system implemented in Rust. It uses the Matrix protocol, a decentralized
communication protocol, for storage and synchronization of comments. This makes
Cactus Comments unique among commenting systems. However, as it is a relatively
new project, it may not have all the features and polish that more established
solutions offer.

2. Plume: Plume is a federated blogging engine implemented in Rust. While it is
   not a standalone commenting system, it includes a built-in commenting
feature. If you decide to use Plume for your blog instead of a static site
generator like Zola, you will get a commenting system as part of the package.

3. Lemmy: Lemmy is a Rust-based, federated link aggregation and discussion
   platform similar to Reddit. While it is not a dedicated commenting system
for blogs, you could potentially use it to host discussions related to your
blog posts, and then embed or link to those discussions from your blog.

It's worth noting that the Rust ecosystem is growing, and new projects may
emerge in the future. However, at this time, Cactus Comments is the primary
Rust-based option specifically focused on providing a self-hosted commenting
system for blogs.

{{ last_msg() }}

Cactus Comments sounds **very** interesting, since I'm already interested in
the Matrix protocol anyhow.  Definitely an option to consider!

Plume sounds like a tangent.  I've decided to go with Zola already, so I don't
think I'll be using Plume.  Lemmy seems similar, but perhaps a bit more
interesting.

I searched Google for a Rust commenting system also, and found an article about
another comment system as well:

{{ first_msg() }}

I found this:
<https://dev.to/netguru/commentable-rs-building-a-serverless-comment-system-in-rust-5egb>

{{ chatgpt_msg() }}

Commentable.rs is a serverless comment system implemented in Rust, as described
in the article you found. The system is built using Rust, AWS Lambda, and AWS
DynamoDB. It is designed to be a lightweight and cost-effective solution for
adding comments to static websites.

To use Commentable.rs, you will need to follow the steps outlined in the
article, which include:

1. Setting up an AWS account and configuring the AWS CLI

2. Creating an AWS DynamoDB table for storing comments

3. Deploying the Rust Lambda function to handle comment submissions and
   retrieval

4. Integrating the commenting system into your static website using JavaScript

Please note that while Commentable.rs is an interesting project, it may not be
as feature-rich or actively maintained as some of the more established
commenting solutions mentioned earlier.

If you're comfortable with AWS and prefer a serverless solution implemented in
Rust, you can give Commentable.rs a try. However, if you're looking for a more
established solution with a larger community, you might want to consider other
options like Remark42, Isso, or Commento.

{{ last_msg() }}

Although this does sound interesting, I think I'll set this one aside for now.
Are there other Rust options out there?

{{ first_msg() }}

What other Rust commenting solutions are you aware of?

{{ chatgpt_msg() }}

As of my knowledge cutoff in September 2021, there are not many mature,
feature-rich Rust-based commenting solutions available. Commentable.rs is one
of the few projects that implement a commenting system in Rust. The Rust
ecosystem is still growing, and more solutions may emerge in the future.

That said, you can always keep an eye on GitHub and other repositories to see
if any new Rust-based commenting systems become available. It's also worth
noting that you can use commenting systems written in other languages with your
Rust-based site, as long as they provide a compatible API or frontend
integration.

For now, if you're looking for a more established commenting solution, you
might want to consider Remark42, Isso, or Commento, as mentioned earlier.
Although they're not implemented in Rust, they are actively maintained and
provide a range of features for managing comments on static websites.

{{ user_msg() }}

You mentioned Cactus Comments, Plume and Lemmy.  Are there other Rust options?

{{ chatgpt_msg() }}

I apologize for the confusion. Cactus Comments is a commenting system built
using the Matrix protocol, and its server component is indeed implemented in
Rust. Plume and Lemmy are Rust-based projects, but they serve different
purposes: Plume is a federated blogging platform, and Lemmy is a federated link
aggregation and discussion platform, similar to Reddit.

As of my knowledge cutoff in September 2021, there are not many other mature
Rust-based commenting solutions available besides Cactus Comments. However, the
Rust ecosystem is growing, and new projects might emerge in the future. You can
keep an eye on GitHub and other repositories for updates on Rust-based
commenting systems.

If you're considering a commenting system for your static site now, Cactus
Comments is a Rust-based option, while Remark42, Isso, and Commento are more
established solutions implemented in other languages.

{{ user_msg() }}

Does Cactus Comments support social login?

{{ chatgpt_msg() }}

As of my knowledge cutoff in September 2021, Cactus Comments does not support
social login directly. Cactus Comments uses the Matrix protocol for its
backend, so users need to have a Matrix account to comment. Matrix accounts can
be created on various homeservers, and some of these homeservers might support
social login. In that case, users can log in to their Matrix account using
social login and then use the same account for commenting on your site through
Cactus Comments.

It's worth noting that the landscape of commenting systems and their features
is always evolving, so it's a good idea to check the Cactus Comments
documentation and updates for the most recent information on supported
features.

{{ last_msg() }}

Hmm, despite how interesting Cactus Comments sounds, lack of support for social
login might be a dealbreaker.

{{ first_msg() }}

Maybe I'll stick with Remark42 or Commento for the social login support.  What
licenses do they use?  Would it be difficult to port one of them to Rust?

{{ chatgpt_msg() }}

Remark42 is licensed under the MIT License, which is a permissive open-source
license. Commento is licensed under the AGPLv3 License, which is a more
restrictive open-source license, requiring that any modifications or derived
works also be licensed under AGPLv3 if distributed.

Porting either Remark42 or Commento to Rust would be a non-trivial task. You
would need to rewrite the entire codebase in Rust, including translating the
logic, data structures, and external library dependencies. It would require a
good understanding of both the original language (Go for Remark42 and
JavaScript for Commento) and Rust, as well as knowledge about the specific
application's architecture and design.

If you are interested in pursuing this project, it would be a significant
undertaking, but it could also be a valuable learning experience and an
interesting contribution to the open-source community. However, if your main
goal is to simply add a commenting system to your blog, it might be more
time-efficient to use one of the existing solutions.

{{ last_msg() }}

Remark42 sounds like the better option, if I might ever want to try porting it
to Rust, or "rewrite it in Rust" as the saying goes.  For now, I'll probably
use Remark42 and consider the possibility of porting it later sometime, or
perhaps never!

Still, if I'm hosting a static site elsewhere (such as GitHub Pages), it would
be nice if the comments could be somehow hosted with the site.  Time to explore
that possibility...

{{ first_msg() }}

Does either of them integrate the comments into the static site once posted, or
would my VPS need to serve comments directly to all clients?

{{ chatgpt_msg() }}

Both Remark42 and Commento serve comments dynamically to the clients, which
means that the comments are not integrated into the static site as a part of
the build process. Instead, the comments are fetched from the server and
displayed on the client-side when a user visits the page.

Your VPS would need to host the commenting system and serve comments directly
to all clients. When a visitor loads your blog post, the static page content is
served from your static site hosting (e.g., GitHub Pages), while the comments
are fetched from your VPS running the commenting system.

This approach has the advantage of keeping your static site generation process
simple and fast while allowing for dynamic, real-time interactions like posting
and fetching comments.

{{ user_msg() }}

Is there a reasonable option for incorporating the comments into the static
site itself so the dynamic code is only needed for actually posting comments,
not reading them?

{{ chatgpt_msg() }}

To incorporate comments into the static site itself, you would need to rebuild
your site each time a new comment is added. This can be done with a combination
of a server-side script and a webhooks mechanism. The general process would
look like this:

1. A user submits a comment through a form on your site.

2. The comment data is sent to your server (VPS), which processes the comment
   and stores it in a database.

3. Your server triggers a webhook, notifying your static site generator (e.g.,
   Zola) to rebuild the site.

4. The site generator pulls the latest comments from the database and
   incorporates them into the static pages.

5. The rebuilt site is deployed, now including the new comment(s).

This approach has its downsides, though. It can be more complex to set up and
maintain, and it might cause delays in comment display, as the entire site must
be rebuilt and redeployed for each new comment.

If you prefer this approach, you could use a combination of existing tools and
custom scripts to achieve it. For example, you could use a headless CMS (like
Netlify CMS) to manage comments and trigger rebuilds via webhooks. Or, you
could build your own custom script to handle comment submissions, store them,
and trigger site rebuilds.

However, considering the potential downsides and complexity, it's generally
more practical to use a dynamic commenting system like Remark42 or Commento,
which separates the comments from the static site generation process and serves
them directly to clients.

{{ user_msg() }}

Why can't the comments be rendered in static HTML separately from generating
the static site and incorporate the static comment HTML somehow without
re-generating the site?

{{ chatgpt_msg() }}

In theory, you could render comments in static HTML separately from generating
the static site and incorporate the static comment HTML without re-generating
the entire site. To achieve this, you would need to implement a few steps:

1. Create a separate static HTML file for each comment or a single file
   containing all comments for a specific page.

2. When a new comment is submitted, your server processes the comment, stores
   it in a database, and generates a new static HTML file containing the
comment or updates an existing file with the new comment.

3. Use JavaScript on the client-side to fetch the static HTML file(s)
   containing the comments and inject them into the appropriate location on
your page.

This approach has some advantages, such as reducing the time it takes to
display new comments since the entire site doesn't need to be rebuilt. However,
it also has a few downsides:

* Increased complexity: This solution requires custom server-side scripts to
  handle comment submissions, store comments, and generate/update static HTML
files.

* More client-side processing: Your users' browsers will need to fetch and
  inject the static HTML comment files, which could increase the time it takes
for comments to load and have an impact on performance.

* SEO: Search engines might not index comments as effectively since they are
  loaded asynchronously and not part of the original static HTML content.

This solution would be a custom hybrid approach, and while it's possible, it
might be more time-consuming and complex to implement than using an existing
dynamic commenting system like Remark42 or Commento.

{{ user_msg() }}

Perhaps the comments could be incorporated into the static HTML directly as a
template substitution after the site as a whole has been generated, and just
repeat that substitution without regenerating the entire site, then check in
the updated page with the new comment into the Git repository and push it to
GitHub so it is live on the site?

{{ chatgpt_msg() }}

Yes, you can incorporate comments into the static HTML directly as a template
substitution after the site has been generated, and update only the relevant
page without regenerating the entire site. Here's a high-level approach to
achieve this:

1. Generate your static site using Zola or another static site generator.

2. Store submitted comments in a database on your server, and have a
   server-side script that fetches the relevant comments for a specific page.

3. Use the server-side script to generate a static HTML file or a JSON file
   containing the comments.

4. Create a script or a tool to substitute the comments into the existing
   static HTML file of the specific page, replacing a placeholder or injecting
them into a specific location on the page.

5. Commit the updated page with the new comment to the Git repository and push
   it to GitHub.

This method can work, but it has some downsides:

* Increased complexity: You would need to develop and maintain custom
  server-side scripts and a tool to handle comment submissions, fetch comments,
and substitute them into the existing static HTML files.

* Manual intervention: You may need to manually trigger the script or tool to
  update the static HTML files, commit them to Git, and push the changes to
GitHub whenever a new comment is submitted.

* Potential Git repository bloat: As you update pages and commit them to the
  Git repository, the repository size will grow over time, possibly leading to
slower clone and pull times.

This custom solution could work for your needs, but it might be more
time-consuming and complex to implement and maintain than using an existing
dynamic commenting system like Remark42 or Commento that handles comment
submissions, storage, and display out of the box.

{{ user_msg() }}

I could imagine the comments being fetched from the site as a JSON file by
client-side JavaScript, but would that be SEO-friendly?

{{ chatgpt_msg() }}

Fetching comments using client-side JavaScript and displaying them dynamically
on the page might not be as SEO-friendly as having the comments directly
embedded in the static HTML. Search engines, such as Google, have become better
at indexing and understanding JavaScript-generated content. However, their
ability to index dynamic content can still be limited compared to static
content.

If SEO is a high priority for your site, it's generally better to have the
comments directly embedded in the static HTML, as this ensures that search
engines can easily crawl and index the content. Using a dynamic commenting
system like Remark42 or Commento, which loads comments using JavaScript, might
be less optimal for SEO purposes.

If you still want to load comments through client-side JavaScript and want to
improve SEO, you could consider using server-side rendering (SSR) or
pre-rendering techniques to generate static HTML pages with comments included.
This approach can help search engines index the content more effectively.

Overall, the best solution for SEO would be to have comments embedded directly
in the static HTML, but it may not be feasible or practical, depending on your
setup and requirements.

{{ last_msg() }}

And now for a bit of a detour...

{{ first_msg() }}

On a separate note, why the hell doesn't HTML support a standard way to
incorporate HTML from a separate HTTPS request into another page using ONLY
HTML/CSS???

{{ chatgpt_msg() }}

The reason HTML and CSS don't have a built-in mechanism for including HTML from
a separate HTTPS request is primarily due to their roles as markup and styling
languages, respectively. HTML is designed to structure content, while CSS is
focused on styling the content. Neither language was designed to manage dynamic
content loading or communication with external resources.

Historically, incorporating external content or executing logic required the
use of a scripting language like JavaScript, which is specifically designed for
such tasks. JavaScript allows you to make AJAX requests to fetch external
content, process it, and then insert it into the DOM. This provides a more
flexible and powerful way to manage dynamic content, including loading content
from external sources.

If you want to include an HTML snippet from another source without using
JavaScript, you can use server-side languages, such as PHP or Python, to fetch
the external content and embed it in your HTML before serving it to the user.
However, this approach is not purely HTML/CSS-based and requires a server-side
processing step.

In summary, HTML and CSS were not designed to handle dynamic content loading or
external resource fetching. These tasks are better suited for JavaScript or
server-side languages, which provide the necessary functionality and
flexibility.

{{ user_msg() }}

HTML has evolved over the years and this sort of template substitution is a
VERY common need (e.g. common site navigation header), it should have been
added years ago.  The only rationale I've seen for it involved avoiding
additional HTTP requests, which is absolutely ridiculous given how many
typically happen already.

{{ chatgpt_msg() }}

You're right that HTML has evolved over the years, and there have been attempts
to address the need for template substitution and reusable components in HTML.
One such approach was the HTML Imports specification, which was part of the Web
Components suite. However, HTML Imports were not widely adopted and have since
been deprecated.

The current recommended approach to create reusable components is to use
JavaScript frameworks or libraries like React, Angular, or Vue.js. These tools
provide powerful and flexible ways to build reusable components, manage state,
and handle user interactions. They leverage JavaScript to dynamically load and
render content, making it easier to build complex and interactive applications.

However, if you're looking for a more lightweight, HTML-based solution, you can
use the **\`\<template\>\`** element in combination with JavaScript to create
reusable components. The **\`\<template\>\`** element allows you to define a
reusable piece of markup that can be cloned and inserted into the document
using JavaScript.

Another solution is to use server-side templating engines like Jinja,
Handlebars, or Liquid, which can handle template substitution and partials
before serving the HTML to the user.

It's worth noting that native HTML templating and component features might
still evolve in the future. The web platform is continuously improving, and new
specifications and proposals may emerge to address these needs more
effectively.

{{ last_msg() }}

Okay, enough venting!

What's this about Git repository bloat?  Just from comments?  Really?  I'm
finding that one hard to believe!

{{ first_msg() }}

Well, that's neither here nor there right now.  If I check in updates to the
page with the new comments, is Git repository bloat really a significant
concern?

{{ chatgpt_msg() }}

Git repository bloat can become a concern if you're constantly updating and
committing large files or making frequent changes to your pages. This can lead
to a larger repository size, slower cloning times, and increased storage
requirements. However, for a blog with comments, the impact is likely to be
minimal, as the text content of comments is typically small.

If you're worried about repository bloat, there are some strategies to mitigate
the issue:

1. **Git Large File Storage (LFS):** If you have large files (e.g., images,
   videos, or other binary files) that change frequently, you can use Git LFS
to store these files more efficiently.

2. **Git history cleanup:** You can perform periodic maintenance on your
   repository using tools like **\`git filter-branch\`** or **\`BFG
Repo-Cleaner\`** to remove unused large files, reduce the number of commits, or
remove sensitive data from your Git history.

3. **Shallow clones:** If you're concerned about cloning times, you can use
   shallow clones (**\`git clone --depth 1\`**) to fetch only the latest commit
history, which reduces the amount of data being transferred.

For a typical blog, though, these measures might not be necessary. The increase
in repository size due to text-based comments is likely to be manageable. If
you start noticing issues with repository size or performance, you can consider
the strategies mentioned above.

{{ user_msg() }}

Can "git gc" be used to generate deltas in a pack file or is that not possible
on the GitHub side?

{{ chatgpt_msg() }}

Yes, **\`git gc\`** (garbage collection) can be used to generate deltas in a
pack file, which helps optimize the Git repository by compressing objects and
reducing its size. The **\`git gc\`** command performs several housekeeping
tasks, such as:

* Removing unreachable objects from the object database

* Compacting loose objects into pack files

* Reusing existing pack files to generate deltas

* Pruning reflog entries

* Expiring old reflog entries

However, when it comes to GitHub repositories, you don't have direct control
over the server-side Git operations. GitHub automatically performs garbage
collection and other housekeeping tasks on their servers to optimize repository
storage.

In your local repository, you can use **\`git gc\`** to optimize storage and
improve performance. It's a good practice to run **\`git gc\`** periodically,
especially if you've made many changes or performed operations like merging and
rebasing that generate a lot of loose objects.

If you notice your GitHub repository is bloated, you can try to clean up your
local repository by running **\`git gc\`**, along with other maintenance
commands like **\`git prune\`**, and then push the cleaned-up repository back
to GitHub. However, keep in mind that this might not have a significant impact
on the server-side repository size, as GitHub has its own garbage collection
policies and processes.

{{ user_msg() }}

Is there any way to trigger "git gc" on the GitHub server?  If I run it on the
client side before the push, would that do any good?

{{ chatgpt_msg() }}

You cannot directly trigger **\`git gc\`** on the GitHub server, as GitHub
automatically runs garbage collection and other housekeeping tasks on their
side. They have their own policies and schedule for running such operations.

Running **\`git gc\`** on the client-side before pushing can still be
beneficial, as it can help optimize your local repository and improve its
performance. It can also reduce the size of the objects you're pushing to the
remote repository on GitHub, which might have a small impact on the server-side
repository size.

However, it's important to note that running **\`git gc\`** on the client-side
won't have a direct or significant impact on the server-side repository size,
as GitHub manages garbage collection and optimization independently.

In summary, it's still a good practice to periodically run **\`git gc\`** in
your local repository to optimize it, but don't expect it to have a substantial
effect on the server-side repository size on GitHub.

{{ last_msg() }}

Yeah, I didn't think that was possible, but you never know!  At any rate, I'm
really not worried about ending up with gigabytes of comments.

Might as well see if ChatGPT has any suggestions on the static HTML idea...

{{ first_msg() }}

If I use Remark42, how can I generate static HTML with the comments to substitute into the page when a new comment is added?

{{ chatgpt_msg() }}

Remark42 does not support generating static HTML with comments out-of-the-box,
but you can achieve this using a custom script. Here's a high-level overview of
the steps you can take:

1. Fetch comments in JSON format from Remark42 API:<br>
Remark42 provides a RESTful API that you can use to fetch the comments for a
specific post. Send a GET request to the following URL, replacing
**\`YOUR_REMARK42_DOMAIN\`**, **\`SITE_ID\`**, and **\`URL\`** with appropriate
values:

```
https://YOUR_REMARK42_DOMAIN/api/v1/find?site=SITE_ID&url=URL
```

2. Parse the JSON and convert it to HTML:<br>
Once you have the JSON data with the comments, you can parse it using a script
(e.g., Python, JavaScript/Node.js) to iterate through the comments and convert
them into the desired HTML structure. You can use any HTML structure and CSS
classes that fit your website design.

3. Replace or insert comments in the static HTML page:<br>
Open your static HTML page and locate the appropriate section where you want to
insert the comments. You can use a placeholder or an HTML comment as a marker.
Your script should then replace or insert the generated HTML with the comments
at the correct location in the file.

4. Update and push changes to your repository:<br>
After updating the static HTML page with the new comments, commit the changes
to your Git repository and push the changes to the remote repository (e.g.,
GitHub Pages).

Remember that this approach requires you to manually run the script each time a
new comment is added. Alternatively, you can automate the process using a
server-side script, webhook, or a continuous integration (CI) pipeline to fetch
new comments and update your static pages automatically.

While this solution allows you to incorporate comments as static HTML, it might
not be the most efficient or scalable approach, especially for websites with
frequent comment activity. Keep this in mind when deciding on a comment system
for your static site.

{{ last_msg() }}

I need to keep monetization in mind also.  I noticed that some Jekyll themes
include AdBlock detection; that seems like a good idea.  I use an ad blocker,
and I read that 33% of Internet users do too.  But I also routinely disable it
for sites with content I want to read.

{{ first_msg() }}

What about AdBlock detection?

{{ chatgpt_msg() }}

AdBlock detection can be useful for publishers who want to detect if users have
an ad blocker enabled and show a message requesting them to disable it or
support the site in another way (e.g., donations or subscriptions). However,
some users may find this intrusive, so it's important to balance the user
experience with the revenue generation.

Here's a simple way to implement AdBlock detection using JavaScript:

{{ ol_open() }}
{{ li() }}
Create an HTML element that mimics an ad:<br>
In your HTML file, add a hidden HTML element with a class name that is
typically blocked by ad blockers, like **\`adsbox\`**. This element acts as
bait for ad blockers:
```html
<div class="adsbox" style="height: 1px; width: 1px; position: absolute; left: -1000px;"></div>
```

{{ li() }}
Add a JavaScript function to check for the presence of the bait element:<br>
In your JavaScript file or within a **\`\<script\>\`** tag, add the following
function to check if the bait element is still in the DOM and visible:

```javascript
function checkAdBlock() {
  const adsBox = document.querySelector('.adsbox');
  if (!adsBox || adsBox.offsetHeight === 0 || adsBox.offsetWidth === 0) {
    // AdBlock is enabled, show a message or execute custom code
    console.log('AdBlock detected.');
  } else {
    // AdBlock is disabled, proceed as usual
    console.log('No AdBlock detected.');
  }
}
```

{{ li() }}
Call the **\`checkAdBlock()\`** function:

Invoke the **\`checkAdBlock()\`** function, preferably after the DOM content
has loaded:

```javascript
document.addEventListener('DOMContentLoaded', checkAdBlock);
```

This code checks for the presence and visibility of the bait element when the
page loads. If the element is not found or is hidden, it assumes that an ad
blocker is enabled and logs a message to the console.
{{ ol_close() }}

In this example, we're just logging a message to the console, but you can
replace that part with custom code to display a message to the user, asking
them to disable their ad blocker or support your site in another way. Keep in
mind that some ad blockers might also block scripts that detect ad blockers, so
your detection method might not always be 100% effective.

{{ last_msg() }}

This is a good stopping point; the topic of tomorrow's post will be the search
for a theme to use for the blog.
