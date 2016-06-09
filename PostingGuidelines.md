What Should Be Posted
=====================
* **DO** post items that would be interesting or useful to the technical / programming community
* **DO** post original blog posts where you have developed a solution to a problem
* **DO** post summaries of other blog posts and how they apply to our work - make sure to link to to the source for these
* **DO** post personal or project achievements if it relates to a particular project or initiative
* **DO** post links to interesting technologies and articles and explain how we might use them. For these be sure to tag them with "InterestingTech" - Tags coming soon
* **DO NOT** post internal documentation even if it does not contain sensitive information. Information such as this should be added in the project documentation.


How To Post
===========
* Checkout the latest version of the [repository](https://github.com/emory-libraries/emory-libraries.github.io)
* Create a new branch for your post
* Make sure you have an entry for your username in `_data/_authors.yml`
* Use octopress to create a new post or page (recommended) `octopress new draft  title-of-post`
    * Run jekyll serve with `-D` to display draft articles, and use [octopress](https://github.com/octopress/octopress) to publish when you are done revising (this will set the date for you) `octopress publish title-of-post`
* To create a new post file manually, create a file in the `_posts` directory of the format `YYYY-MM-DD-TITLE.md` in the new file, include the below header information. Note the author field links to the reference in `_data/_authors.yml`:
```
---
layout: post
title: THE TITLE
tags:
    - jekyll
authors:
    - yang_li
---
```
* Write your post
* Tags should be added in lower case, slug format; if you want to add a display name or description for a tag, add or update the entry in
    `_data/_tags.yml`, which will be displayed on the tag index page.
* To see your post on a your local version of the blog before you publish it,  run `bundle exec jekyll serve` and and go to http://localhost:4000 (by default).
*  On GitHub create a [pull request](https://github.com/emory-libraries/emory-libraries.github.io/compare?expand=1) for others to review. Posts that fall under the "interesting tech" category do not need to be reviewed, thus they can be committed without a a pull request.
*  All can ask questions and add comments, but the Ringleader for the iteration has the responsibility to review and merge (or not merge) the pull request to the main branch.  If the post is by the current Ringleader, or the Ringleader is unavailable due to being sick or on vacation, the responsibility falls to the next person on the list.
