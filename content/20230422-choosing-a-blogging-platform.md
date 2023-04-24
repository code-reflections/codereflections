+++
title = "Choosing a blogging platform."
date = 2023-04-22
slug = "choosing-a-blogging-platform"
path = "/2023/04/22/choosing-a-blogging-platform/"

[taxonomies]
categories = ["Meta"]
tags = ["ChatGPT", "CodeReflections", "Zola"]
+++

After my [initial exploration of blogging
platforms](/2023/04/20/how-the-sausage-is-made/) and [finding a VPS hosting
provider](/2023/04/21/searching-for-a-hosting-provider/), I needed to decide
which blogging platform to use.  ChatGPT continued to assist with the
decision-making process.

<!-- more -->

Earlier in the conversation, ChatGPT mentioned Zola and that it offers Sass
compilation out of the box.  I didn't recognize that offhand, so I asked.

{{ first_msg() }}

You said that Zola offers Sass compilation out of the box. What is Sass
compilation?

{{ chatgpt_msg() }}

Sass (short for Syntactically Awesome Style Sheets) is a preprocessor scripting
language that extends CSS (Cascading Style Sheets). Sass allows developers to
use variables, nested rules, mixins, and functions, making it easier to write
and maintain complex CSS code. Sass code needs to be compiled into standard CSS
before it can be used by web browsers.

Sass compilation refers to the process of converting Sass code into CSS. This
is typically done using a build tool or task runner, such as Gulp, Grunt, or
Webpack. However, some static site generators, like Zola, offer built-in Sass
compilation, meaning you don't need to set up a separate build tool or process
for it. This can make it more convenient to work with Sass when building a
website or a blog, as the compilation step is handled automatically by the
static site generator.

{{ user_msg() }}

Should I bother using Sass?

{{ chatgpt_msg() }}

Using Sass can be beneficial for your project depending on your requirements
and familiarity with CSS. Here are some reasons to consider using Sass:

1. Maintainability: Sass allows you to use variables, which can make it easier
   to manage and maintain your stylesheets. For example, you can define colors,
font sizes, and other frequently used properties as variables and reuse them
throughout your styles.

2. Modularization: You can split your Sass code into multiple files and use the
   **\`@import\`** directive to include them in the main stylesheet. This can help you
organize your code better and promote modular design.

3. Nested syntax: Sass enables you to nest selectors within one another, which
   can make your code more readable and easier to maintain by closely mimicking
the structure of your HTML.

4. Mixins and functions: Sass provides mixins and functions that allow you to
   reuse blocks of code and perform calculations. This can help you write more
efficient and DRY (Don't Repeat Yourself) code.

5. Extensibility: Sass provides advanced features like loops and conditional
   statements that can help you create complex styles with minimal code.

However, if your project is small, or you're not familiar with Sass, it may be
an unnecessary addition. For simple projects, plain CSS might be sufficient.
Additionally, learning Sass syntax and setting up the compilation process can
add extra complexity to your project.

In summary, Sass can be beneficial for larger projects or when you want to
improve the maintainability and organization of your styles. However, for
smaller projects or when you're less experienced with CSS, sticking to plain
CSS might be more appropriate.

{{ last_msg() }}

Okay, sounds useful.  I'll have to keep that in mind.  Meanwhile, I wanted to
compare the options ChatGPT previously suggested.

{{ first_msg() }}

How do Jekyll, Zola and Cobalt compare with each other?

{{ chatgpt_msg() }}

Jekyll, Zola, and Cobalt are all static site generators, but they have some
differences in terms of features, performance, and the languages they are built
on. Here's a comparison of the three:

<ol>
<li>Language and Performance:

<ul>
<li>Jekyll is written in Ruby and uses the Liquid templating engine. It is one
of the most popular static site generators and has a large community and
ecosystem. However, it can be slower in comparison to Zola and Cobalt,
especially for larger sites.
<li>Zola is written in Rust and uses the Tera templating engine. Rust is known
for its performance, and as a result, Zola can build sites much faster than
Jekyll. This can be a significant advantage for larger projects.
<li>Cobalt is also written in Rust and uses the Liquid templating engine. It
offers good performance due to Rust but may not be as fast as Zola due to
differences in the templating engine.
</ul>

<li>Features:

<ul>
<li>Jekyll offers a wide range of features, including support for Sass
compilation, syntax highlighting, and built-in support for blogging with
pagination. It also has a vast library of plugins and themes, thanks to its
large community.
<li>Zola has a similar feature set to Jekyll but with a focus on performance.
It offers built-in support for Sass compilation, syntax highlighting,
taxonomies, and pagination. It also has shortcodes and templates for common
tasks.
<li>Cobalt provides a more minimalistic set of features compared to Jekyll and
Zola. It does not have built-in support for Sass compilation or syntax
highlighting but supports blogging and pagination.
</ul>

<li>Community and Ecosystem:

<ul>
<li>Jekyll has the largest community and ecosystem among the three, with a vast
library of plugins, themes, and resources. It's been around the longest and has
strong support from its community.
<li>Zola is gaining popularity but has a smaller community and ecosystem
compared to Jekyll. There are fewer themes and plugins available, but the
community is growing.
<li>Cobalt has the smallest community and ecosystem among the three. It has
limited themes and plugins, which might be a drawback if you're looking for
extensive customization options.
</ul>

In summary, Jekyll is a popular choice with a large community and ecosystem,
but it may be slower for larger projects. Zola offers better performance and a
similar feature set but has a smaller community. Cobalt is a more minimalistic
option with fewer features and a smaller community. Choosing between them
largely depends on your project requirements, preferred language, and the level
of community support and customization options you need.

{{ last_msg() }}

Jekyll does sound like a very nice option, but Rust is one of the two languages
that I'm most interested in, so I wanted to give one of those options a try.  I
wasn't familiar with the Liquid templating engine, nor with the Tera templating
engine.

{{ first_msg() }}

I don't know anything about the Liquid templating engine.  Tell me about it.
How does it compare with Tera?

{{ chatgpt_msg() }}

Liquid and Tera are both templating engines used to generate HTML content for
static site generators. Here's a comparison between the two:

<ol>
<li>Liquid:

<ul>
<li>Liquid is a Ruby-based templating language developed by Shopify. It is used
in various projects, including Jekyll and Cobalt.
<li>It is designed to be simple and easy to learn, with a focus on safety and
security.
<li>It uses a combination of tags, filters, and objects to process and render
templates.
<li>Tags are used for logic and control structures, such as loops and
conditionals. Filters are used to modify the output of an object, and objects
represent the content being output.
<li>Liquid is considered safe because it does not allow arbitrary code
execution, which can help prevent security vulnerabilities.
<li>It has a wide range of plugins and a large community, making it easier to
find resources and support.
</ul>

<li>Tera:

<ul>
<li>Tera is a Rust-based templating language inspired by Jinja2 and the Django
template language. It is used in Zola.
<li>It is designed for performance and safety, leveraging the speed of Rust.
<li>Tera uses similar concepts to Liquid, such as tags, filters, and objects,
to process and render templates.
<li>It also supports template inheritance, which allows you to create a base
template and extend it with child templates. This can help you create more
maintainable and DRY (Don't Repeat Yourself) code.
<li>Like Liquid, Tera is considered safe because it does not allow arbitrary
code execution.
</ul>
</ol>

Comparison:
<ul>
<li>Both Liquid and Tera are designed for safety and simplicity, and both use
similar concepts like tags, filters, and objects.
<li>Liquid has a larger community and a wider range of plugins, thanks to its
use in Jekyll and Shopify.
<li>Tera is focused on performance and is written in Rust, which can make it
faster in some cases.
<li>Tera supports template inheritance, which can help create more maintainable
and DRY code.
</ul>

Choosing between Liquid and Tera depends on the static site generator you
prefer and the language you are more comfortable with. If you're using Jekyll
or Cobalt, you'll work with Liquid, whereas if you choose Zola, you'll use
Tera. Both are powerful and safe templating engines that can help you build
static websites efficiently.

{{ last_msg() }}

Tera is implemented in Rust, focused on performance and supports template
inheritance.  Sounds good to me!  I don't see much reason to use Cobalt, since
it has the smallest community and ecosystem, and a minimalistic feature set.
Zola seems like the best choice for me, and it has a similar feature set to
Jekyll, but Jekyll is more popular with a larger community and ecosystem.  If I
pick Zola over Jekyll, will I regret it?

{{ first_msg() }}

Will I lose any important features or functionality if I choose Zola over
Jekyll?

{{ chatgpt_msg() }}

While both Jekyll and Zola are powerful and feature-rich static site
generators, there are some differences in functionality that you should be
aware of when choosing between the two:

<ol>
<li>Language and ecosystem:

<ul>
<li>Jekyll is written in Ruby and has a large plugin ecosystem, which means you
can easily extend its functionality using various plugins developed by the
community.
<li>Zola is written in Rust, which is known for its speed and safety. However,
it doesn't have as large of a plugin ecosystem as Jekyll. This means that there
might be fewer ready-made solutions for specific use cases, and you may need to
implement certain functionality on your own.
</ul>

<li>Theme availability:

<ul>
<li>Jekyll has a larger community, which has resulted in a greater number of
themes available for use. This can make it easier to find a suitable theme for
your blog.
<li>Zola has fewer themes available, which means you might need to create your
own theme or modify an existing one to fit your needs.
</ul>

<li>Hosting options:

<ul>
<li>Jekyll has native support for GitHub Pages, which makes it easy to deploy
and host your site for free on GitHub.
<li>Zola does not have native support for GitHub Pages, but you can still use
it with GitHub Pages by generating the static files and pushing them to your
repository. This requires an additional step, but it is not overly complicated.
</ul>

<li>Learning curve:

<ul>
<li>Jekyll uses the Liquid templating language, which might be easier to learn
for some users, especially if they have experience with Ruby or other template
languages like Jinja2.
<li>Zola uses the Tera templating language, which is inspired by Jinja2 and
Django. While it is still relatively easy to learn, some users might prefer the
familiarity of Liquid.
</ul>
</ol>

Overall, while Zola may lack some of the extensive plugin ecosystem and theme
availability of Jekyll, it still offers a powerful and fast static site
generator with a focus on simplicity and performance. If you're comfortable
with Rust and don't mind a smaller community and fewer ready-made solutions,
Zola can be an excellent choice. However, if you prefer a larger community, a
wider range of plugins and themes, and native support for GitHub Pages, Jekyll
might be the better option.

{{ user_msg() }}

Are there any Jekyll plugins particularly of special interest that don't have
equivalents available for Zola?

{{ chatgpt_msg() }}

While Zola does have built-in features that cover many use cases, there might
be some Jekyll plugins with unique functionality that don't have direct
equivalents in Zola. Some examples include:

1. jekyll-admin: This plugin provides a user interface to manage your Jekyll
   site, including editing content, managing drafts, and previewing changes.
There is no direct equivalent for Zola, and you'll need to rely on your text
editor or other content management tools.

2. jekyll-archives: This plugin automatically generates archive pages for your
   Jekyll site, such as monthly or yearly archives, tag archives, or category
archives. Zola has support for taxonomies (tags and categories) out-of-the-box,
but it doesn't have built-in support for generating date-based archives.

3. jekyll-paginate: This plugin provides pagination functionality for your
   Jekyll site. Zola has built-in support for pagination, but the
implementation and customization options might differ from those offered by the
jekyll-paginate plugin.

4. jekyll-redirect-from: This plugin allows you to easily create redirect pages
   for changed or moved content. In Zola, you'll need to handle redirects
manually, either by creating a custom short code or configuring redirects on
your web server.

5. jekyll-assets: This plugin helps with asset management, such as CSS,
   JavaScript, and image files. It provides features like asset fingerprinting,
compression, and caching. Zola has some built-in features for asset management,
like Sass compilation, but it doesn't provide the same level of functionality
as jekyll-assets.

While these plugins might not have direct equivalents in Zola, there are often
alternative solutions or workarounds for achieving similar functionality. If a
specific Jekyll plugin is crucial to your project, consider whether the
features it provides can be replicated in Zola or if sticking with Jekyll might
be a better choice for your needs.

{{ last_msg() }}

None of these seem like dealbreakers to me.  What about the themes?

{{ first_msg() }}

Can a Jekyll theme be ported to Zola?

{{ chatgpt_msg() }}

Yes, a Jekyll theme can be ported to Zola, but it requires some manual work.
Jekyll and Zola have different templating engines and folder structures, so
you'll need to make adjustments to the theme to make it compatible with Zola.
Here's a rough outline of the steps involved:

1. Folder structure: Zola has a different folder structure than Jekyll. Create
   a new Zola project and reorganize the theme files to fit Zola's folder
structure. Mainly, you'll need to move the layout files to the templates
folder, and assets like CSS, JavaScript, and images to the static folder.

2. Templating engine: Jekyll uses the Liquid templating engine, while Zola uses
   Tera. You'll need to convert the Liquid templates to Tera templates.
Although both engines share similarities, there are differences in syntax,
filters, and tags. Update the template files to use Tera syntax and replace any
Liquid-specific functionality with Tera equivalents.

3. Frontmatter: Update the frontmatter in the content files to match Zola's
   TOML or YAML format.

4. Pagination and taxonomies: If the Jekyll theme uses pagination or taxonomies
   (categories, tags), configure Zola to handle these features. Zola has
built-in support for pagination and taxonomies, but you'll need to set them up
according to the theme's requirements.

5. Plugins: If the Jekyll theme relies on any plugins, you'll need to find
   equivalent functionality in Zola or create custom shortcodes or components
to replicate the plugin features.

6. Sass/SCSS: If the Jekyll theme uses Sass or SCSS, you can take advantage of
   Zola's built-in Sass compilation. Make sure to update any import paths in
your Sass files to match Zola's folder structure.

7. Test and adjust: Once you've made all the necessary changes, test the Zola
   theme thoroughly to ensure everything works as expected. Make any
adjustments or bug fixes as needed.

Porting a theme from Jekyll to Zola can be a time-consuming process, but it
allows you to use your preferred theme with the benefits of Zola's features and
performance.

{{ last_msg() }}

Okay, I'd rather not start out by trying to port a theme, but it's a
possibility to keep in mind.  But what is this SCSS?

{{ first_msg() }}

What is SCSS?

{{ chatgpt_msg() }}

SCSS (Sassy CSS) is a syntax for Sass (Syntactically Awesome Style Sheets),
which is a CSS preprocessor. It extends the capabilities of CSS by introducing
features like variables, nested rules, mixins, functions, and more. SCSS aims
to make working with CSS more maintainable, structured, and efficient.

SCSS is similar to CSS in terms of syntax and uses curly braces and semicolons,
which makes it easier for developers familiar with CSS to adapt to. Here's a
quick comparison of CSS and SCSS:

CSS:

```css
.navigation {
  background-color: #333;
  padding: 20px;
}

.navigation a {
  color: white;
  text-decoration: none;
  padding: 5px;
}
```

SCSS:

```scss
$bg-color: #333;
$link-color: white;

.navigation {
  background-color: $bg-color;
  padding: 20px;

  a {
    color: $link-color;
    text-decoration: none;
    padding: 5px;
  }
}
```

In the SCSS example, we use variables ($bg-color and $link-color) to store
color values and nested rules for .navigation a. These features make it easier
to maintain and organize your styles.

When SCSS is compiled, it generates standard CSS that browsers can understand.
Using tools like Zola or other build systems, you can easily integrate SCSS
compilation into your development workflow.

{{ last_msg() }}

Sounds useful.  I figured this question was a long shot:

{{ first_msg() }}

Is there any automated tool to convert Liquid templates to Tera?

{{ chatgpt_msg() }}

There isn't a dedicated automated tool to directly convert Liquid templates to
Tera templates. Since Liquid and Tera have differences in syntax and
functionality, it's difficult to create a fully automated conversion tool that
handles all possible cases.

However, you can manually convert Liquid templates to Tera templates by
following these general steps:

1. Study the differences between Liquid and Tera syntax and understand their
   respective features.

2. Replace Liquid tags, filters, and expressions with their Tera equivalents.

3. Test the converted templates to ensure they produce the desired output.

It's essential to familiarize yourself with both Liquid and Tera documentation
to understand how each template language works and make the necessary
adjustments during the conversion process.

Liquid Documentation: **<https://shopify.github.io/liquid/>**<br>
Tera Documentation: **<https://tera.netlify.app/docs/>**

{{ last_msg() }}

I decided to try Zola, but there was still the comment system to consider.
That will be the subject of [tomorrow's
post](/2023/04/23/choosing-a-comment-system/).
