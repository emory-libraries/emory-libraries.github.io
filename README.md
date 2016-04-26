# Getting started

Install dependencies using bundle (recommended):

    bundle install

Run jekyll and view at http://localhost:4000 (by default):

    bundle exec jekyll serve

To use octopress to create a new post or page (optional but recommended), e.g.:

    octopress new draft  title-of-post

Run jekyll serve with `-D` to display draft articles, and use [octopress](https://github.com/octopress/octopress) to publish when you're done revising (this will set the date for you):

    octopress publish title-of-post

The first time you add an article you should also add yourself to the `_authors.yml` file in the _data directory.  Make sure to set yourself
as the post article.

## documentation and links

* [jekyll](http://jekyllrb.com/)
* [liquid](https://shopify.github.io/liquid/) (template language used by jekyll)
* [octopress](https://github.com/octopress/octopress)

* * *

# Minimal Mistakes

**[Minimal Mistakes](http://mmistakes.github.io/minimal-mistakes)** is a two column responsive Jekyll theme perfect for powering your GitHub hosted blog built. Compatible with Jekyll 3.0 and up.

## Minimal Mistakes is all about:

* Responsive templates. Looking good on mobile, tablet, and desktop.
* Gracefully degrading in older browsers. Compatible with Internet Explorer 8+ and all modern browsers.
* Minimal embellishments -- content first.
* Optional large feature images for posts and pages.
* Simple and clear permalink structure.
* [Custom 404 page](http://mmistakes.github.io/minimal-mistakes/404.html) to get you started.
* Support for Disqus Comments

![screenshot of Minimal Mistakes theme](http://mmistakes.github.io/minimal-mistakes/images/mm-theme-post-600.jpg)

See a [live version of Minimal Mistakes](http://mmistakes.github.io/minimal-mistakes/) hosted on GitHub.

## Getting Started

Minimal Mistakes takes advantage of Sass and data files to make customizing easier. These features require [Jekyll 2.x](https://github.com/mmistakes/minimal-mistakes/releases/tag/2.1.3) and will not work with older versions of Jekyll.

To learn how to install and use this theme check out the [Setup Guide](http://mmistakes.github.io/minimal-mistakes/theme-setup/) for more information.
