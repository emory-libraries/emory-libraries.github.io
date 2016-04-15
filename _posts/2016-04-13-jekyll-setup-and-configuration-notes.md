---
layout: post
title: Jekyll Setup and Configuration Notes  
categories: [Jekyll]
author: yang_li
---

Title:  Jekyll Setup and Configuration Notes  
Author: Yang Li  
Date:   April 13, 2016  


# Background

We have been thinking about using a blog system to collect and organize developer notes, and in order to do so we think that we could use a Jekyll site hosted on our GitHub pages.


# Jekyll Setup

GitHub offers an excellent tutorial that guides us through the installation and deployment process. We followed the articles in the following link to have our Jekyll site initialized.
https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/


# Remote Repository

A problem we ran into was that when we do ```bundle exec jekyll serve``` in a locally initialized enviornment (unpublished git repository) Jekyll would complain about ```jekyll 2.4.0 | Error:  undefined method `[]' for nil:NilClass```

The reason behind this is a bug in one of the Jekyll dependencies. The dependency is looking for the remote git repository but if you don't have the repository published it would fail. So what you would need to do is to run ```git remote add origin [your repository]``` to get it started.


# Jekyll Themes

Rebecca recommended some themes that can be very good for us to style our Jekyll site and here are the links:

* [minimal-mistakes](http://mmistakes.github.io/minimal-mistakes/theme-setup/)
* [skinny-bones](https://github.com/mmistakes/skinny-bones-jekyll)
* [Jekyll Themes](http://jekyllthemes.org/)
* [JekyllThemes.io](http://jekyllthemes.io/)


# Developer's Recipe for Setting up a Jekyll Site

* follow GitHub setup guide to have a repository initialized
* visit https://github.com/mmistakes/minimal-mistakes
* git clone git@github.com:mmistakes/minimal-mistakes.git
* gem install bundler
* bundle
* update config.yml, add navigation, and replace demo posts and pages with your own.
* customize logo, style, images, authors, and remove the default sample posts
* deploy to GitHub by pushing the code up


# Other Useful Links

* [Create a Multi Blog Site with Jekyll](https://www.garron.me/en/blog/multi-blog-site-jekyll.html)
* [How can I have multiple authors for one post in Jekyll?](http://stackoverflow.com/questions/15189008/how-can-i-have-multiple-authors-for-one-post-in-jekyll)
