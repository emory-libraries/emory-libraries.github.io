---
layout: post
title: Front-end Testing Research Notes
tags: [front-end, testing, ui, packages, research]
authors:
    - yang_li
---

Front-end testing is not quite the same as unit testing in the backend world because of the user interactions that happen in a browser (and you know, in reality its multiple browsers of different versions on different devices). That leads to this topic about front-end testing kit research.

There are a few awesome blogposts and talks out there about front-end testing albeit the fact that front-end testing is a relatively new topic. In the presentation by Chris Ruppel, he mentioned that there are a few reasons why we should use front-end testing:

* Minor CSS changes that throw things off
* Changes to JS files that break things
* Aggregates changing when not necessary
* Performance regressions

By reading his [blog](http://rupl.github.io/frontend-testing/) I figured that we can break down front-end testing into two sub groups of testing, one being functional/unit testing and the other being performance testing. Both paths lead us to a same destination that is a better development workflow with regression testing: no fear of adding features might break stuff and productivity.

I naively characterize the "functional/unit testing" as one kind of testing that will make sure the code still works, and this includes the aesthetics, presentation on the page, widget functionalities, responsiveness just to name a few.

The other "performance testing" aims at improving front-end performance. Some might argue that the performance side can be separated from traditional unit testing of for example the backend, but I think it doesn’t hurt to have it here because it can also be automated and streamlined with testing tools and aids such as grunt, gulp, and your favorite continuous integration tools.

## Tools and Services

### Performance

**[BrowserSync](https://www.browsersync.io/)**  
BrowserSync, the most amazing way to develop real-time on multiple devices.

**[WebpageTest](http://www.webpagetest.org/)**  
WEBPAGETEST, it runs a series of performance profiling tasks and generate reports that detail what and how long each step is and takes. It even takes screenshots and record videos for us to help us diagnose.

**[YSlow](http://yslow.org/)**  
YSlow is developed by Yahoo when they were the performance king. This is still a very handy I tried as a Chrome addon.

**Ember Inspector**  

> The Ember Inspector is a plug-in for the Chrome developer tools that makes understanding and debugging your Ember.js application a snap.

**Uncss**  

> UnCSS is a tool that removes unused CSS from your stylesheets. It works across multiple files and supports Javascript-injected CSS.
The process by which UnCSS removes the unused rules is as follows:

* The HTML files are loaded by PhantomJS and JavaScript is executed.
* Used stylesheets are extracted from the resulting HTML.
* The stylesheets are concatenated and the rules are parsed by css-parse.
* document.querySelector filters out selectors that are not found in the HTML files.
* The remaining rules are converted back to CSS.

**Chrome Inspector**  
Chrome is my favorite browser for development purpose and a big part of the reason is its powerful inspector. I used the profiling feature before and find it very helpful. Here is an intro that offers a quick guide to the profiling tool. [Google Chrome Inspector Timeline](https://developer.chrome.com/devtools/docs/timeline)

### Task Runners

**Grunt**   
Grunt is basically a task scheduler/runner that can help you run a series of front-end tasks. It's JS friendly and is designed for front-end dependency management tools such as npm.  

From the official website:  

> Each time grunt is run, it looks for a locally installed Grunt using node's require() system. Because of this, you can run grunt from any subfolder in your project.
If a locally installed Grunt is found, the CLI loads the local installation of the Grunt library, applies the configuration from your Gruntfile, and executes any tasks you've requested for it to run. To really understand what is happening, read the code.

[Get Started](http://gruntjs.com/getting-started)  
[Grunt for People Who Think Things Like Grunt are Weird and Hard](https://24ways.org/2013/grunt-is-not-weird-and-hard/)

**Gulp**
A good introduction blog I read is:  
[Gulp for Beginners](https://css-tricks.com/gulp-for-beginners/)

**Difference**  
There is a great article I found on Medium that details the difference between grunt and gulp.  
[Gulp vs Grunt. Why one? Why the Other?](https://medium.com/@preslavrachev/gulp-vs-grunt-why-one-why-the-other-f5d3b398edc4)  

The take-home message however is that Grunt is more about configuration and we can easily get stuff running and going; gulp can be more flexible and would require some more setup and code writing to get it started.

**Install grunt.js**  
This is a task runner that will help us automate processes in the front-end code base
Tasks such as running JSHint, compile assets, minify JS

**Get grunt**  

```shell
npm install grunt --save-dev
```  

**Get grunt-cli**  

```shell
npm install grunt-cli --sav-dev
```

**Get a grunt module such as jshint**

```shell
npm install grunt-contrib-jshint --save-dev
npm install grunt-contrib-uglify --save-dev
```

There are a few tasks that grunt and its community offers to developers, such as these below:  

```shell
grunt-contrib-clean
grunt-contrib-watch
grunt-contrib-compass
grunt-contrib-imagemin
grunt-contrib-concat
grunt-concurrent
grunt-svgmin
grunt-jekyll
```

Correspondingly we can install them with these lines:

```shell
npm install grunt-contrib-clean --sav-dev
npm install grunt-contrib-watch --sav-dev
npm install grunt-contrib-compass --sav-dev
npm install grunt-contrib-imagemin --sav-dev
npm install grunt-contrib-concat --sav-dev
npm install grunt-concurrent --sav-dev
npm install grunt-svgmin --sav-dev
npm install grunt-jekyll --sav-dev
```

These above tasks can be a good starting point to learn and use Grunt. We can schedule other tasks that can be helpful for front-end deployment, performance improvement, garbage removal etc.

### Casper.js

> CasperJS is an open source navigation scripting & testing utility written in Javascript for the PhantomJS WebKit headless browser and SlimerJS (Gecko). It eases the process of defining a full navigation scenario and provides useful high-level functions, methods & syntactic sugar for doing common tasks such as:

* defining & ordering browsing navigation steps
* filling & submitting forms
* clicking & following links
* capturing screenshots of a page (or part of it)
* testing remote DOM
* logging events
* downloading resources, including binary ones
* writing functional test suites, saving results as JUnit XML
* scraping Web contents

Above information is from the official website.

In simple words Casper.js is running on Phantom.js. Phantom.js is like a ghosty browser that we cannot see but under the hood is a Webkit based browser. We can operate (e.g. click, scroll) by writing instructions (code) so that the tests are more repeatable, manageable, and development friendly. We can write tasks in Casper.js to perform functional testing.

Some of the key points with CasperJS that I tried:    

* CasperJS is a wrapper that sits on top of the PhantomJS
* Can render screenshots
* Code actions with PhantomJS
* Selenium is similar
* Casper is better in the case that for people who can use jQuery
* Run same test with multiple screen sizes
* Test complex features or components
* Automate complex user actions
* Test content creation, transactions, other features


### QUnit and Unit Testing in Front-end

This presentation is a good intro to unit testing and I've also extracted some examples as notes: [Unit Testing QUnit](http://benalman.com/talks/unit-testing-qunit.html#16)

```shell
// You can either set an expectation (number) like this.
test("test name", function() {  
  expect(3); // QUnit expects 3 assertions in this test.  
});

// Or like this.
test("test name", 3, function() {  
  // QUnit expects 3 assertions in this test.  
});
```

The meaning of atomic:
atomic basically means you cannot disintegrate or break down into smaller pieces.
`a = 1;`
that’s it. there are no intermediate steps (at least not on this level)

I like this description which is:

> Unit testing makes sure you are using quality ingredients. Functional testing makes sure your application doesn't taste like crap. And I am pretty sure that someone in front of the screen reading this article want to jump up and start yelling but when there are many constraints we would need to unfortunately make some compromises and prioritize what can make a difference.

### Summary
They are attacking different problems. Since PhantomJS runs perfectly on the command-line, it is suitable as the first layer of smoke testing, whether as part of development workflow and/or in a continuous integration server. Selenium targets multiple browsers and hence it is very useful to ensure cross-browser consistency and carry out extensive testings across different operating systems.

[Webcast: PhantomJS, CasperJS, Screenshot Comparison, and Ghost Inspector](https://ghostinspector.com/blog/webcast-phantomjs-casperjs-screenshot-comparison-and-ghost-inspector/)


## Others

### Travis CI

[Integrate Travis CI with your GitHub repo](https://github.com/mbonaci/mbo-storm/wiki/Integrate-Travis-CI-with-your-GitHub-repo)

[Using Travis Continuous Integration for Your Open Source Project](https://blog.dylants.com/2013/03/21/using-travis-continuous-integration-for-your-open-source-project/)

### Casper vs. Others

[CasperJS vs. Jasmine vs. Mocha in a Chart](http://www.slant.co/topics/1489/compare/~mocha_vs_jasmine_vs_casperjs)

### Other JS render engines
* SlimerJS
* TrifleJS
