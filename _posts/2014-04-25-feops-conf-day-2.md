---
layout: post
title: FeOpsConf Notes, Day 2
published: true
---

## Delivering the Goods in Under 1000ms

*Paul Irish, Google*

Identify a metric to move the needle of a business need/goal.

Speed Index - Lower is better. Goal should be under 1000.

Total page size and Number of requests are equally important. Latency has a direct linear correlation to page load time. Latency in wireless is painful.

<!--more-->

Video streaming is bandwidth limited. Web browsing is latency limited.

TCP Slow Start ramps up the amount of data transferred over time.

* Eliminate render blocking JavaScript
* Minimize render blocking CSS - separate critical css from non-critical

**Tools**

* [WebPageTest](http://webpagetest.org) - tool for measuring page load and request times with webpage thumbnails.
* [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) - best practices for desktop and mobile.

-----

## The Rise of Front End Tooling

*Mikeal Rogers, Digital Ocean*

About a third of the activity on npm is related to front end tooling. Mostly Grunt; Gulp had a big spike.

Development tools for front end are growing faster than back end and node development is growing faster than any other technology.

**Tools**

* [Perspective](http://pixxa.com/) - presentation tool for displaying charts

-----

## Reducing Complexity with a Component API

*Ian Feather, Lonely Planet*

* Shared Layer - High reuse, Strong caching, High risk
* App Layer - Low reuse, Weak caching, Low risk
* Component Layer - High reuse, Low risk

A Style Guide isn't the mechanism.

**Benefits**

* Happier developers
* Visual consistency
* Refactor easily
* Less tweaking at App layer (in theory)

**Tools**

* [Rizzo](http://rizzo.lonelyplanet.com/styleguide/) - Lonely Planet's styleguide.

-----

## Automating a Maintainable Front End

*Rachel Myers & Emily Nakashima, GitHub*

[Slides & Resources](http://bit.ly/almost-everything)

**Stages of Performance Optimization**

1. configuration for bottlenecks
2. refactor bottlenecks
3. performance-minded development
4. repeat 3 for as long as you can before going back to 1 & 2

You could use Modernizr.load or Require.js to load individual polyfills, but it can delay load time and adds overhead.

**Sunset Tests**

Put browser support expiration into unit tests. That way the build fails on an agreed upon expiration date.

Know what browsers you support and enforce that thru code/tests.

**Tools**

* [ucss](https://github.com/operasoftware/ucss)
* [uncss](https://github.com/giakki/uncss)
* [dom-prof](https://github.com/josh/dom-prof) - phantomjs crawler
* [DOM Monster](http://mir.aculo.us/dom-monster/) - bookmarklet

-----

## Continuous Translation

*Burak Yigit Kaya, Disqus*

Community sourced translators.

Translations are dependencies.

Additional considerations for RTL support and Date/Time formatting.

**Tools**

* [Transifex](https://www.transifex.com/) - SaaS translation provider
* [grunt-i18n-abide](https://github.com/mozilla/grunt-i18n-abide) - Grunt task for build translations
* [R2](https://github.com/ded/R2) - library to automatically switch styles from LTR to RTL
* [moment.js](http://momentjs.com/) - really good language support

-----

## The Dark Side

*Martin Kleppe, Ubilabs*

[Website](http://aem1k.com/)

-----

## Apps that Talk Back

*Rebecca Murphey, BazaarVoice*

### They keep you from doing bad things

* Git hooks - for enforcing style rules and running tests pre-push
* Grunt - for running jshint during development

Build assertions into error handling; provides sane error messages.

### They tell when you do a bad thing

Logging errors with more detail, categorization, hashed stack traces.

### Identify things before they are things

Use Istanbul to see what code is actually being executed.

### Help fix the things

Production swallows errors, but a cookie can be set to enable verbose logging at any time.

**Tools**

* [node-jscs](https://github.com/mdevils/node-jscs) - Code style checker
* [istanbul](https://github.com/gotwarlost/istanbul) - JavaScript code coverage

-----

## Building a Large Scale Synthetic Performance Lab

*Amiya Gupta, Microsoft*

**Lessons Learned**

1. Synthetic data is fundamentally different from real user data
1. Focus on consistency
1. Larger sample size isn't always the answer

Navigation Timing API is supported by most browsers (not Safari).

Benchamrking is instantaneous. Monitoring includes dimension of time and location. Synthetic measurements enable deeper analysis by eliminating variables; trade accuracy for consistency.

Minimum PLT - there's a hard lower limit to how quickly a page could possibly load; no upper limit.

Benchmark Page - Simple HTML page with a few images, no CSS or JS. Simulations against the Benchmark Page tell you what your Minimum PLT is.

Measure -> Analyze -> Improve -> Repeat

Benchmark page can also indicate problems with network and hardware (ie, Latency, Packet Loss, CDN Routing).

Synthetic environments can suffer from cold server cache and DNS timeout.

**Tools**

* [Boomerang](http://yahoo.github.io/boomerang/doc/) - measure webpage performance on client and report back to server.

-----

## Introducing RequireJS into a Large Codebase. Delicately.

*Dan Lee & Chris Chen, Yammer*

Shim `require` & `define` to avoid errors on non-RequireJS pages.

Target one controller at a time to progressively add AMD-ification.

**Takeaways**

1. Isolation - find a small slice of your app to start
2. Iteration - chart out the path from the small slice to the whole pie
3. Minimize disruption - don't break the dev environment for other parts of the app

"Code in transition is OK."" Developers have a desire for consistency, but innovation necessitates transitional steps.

-----

## It's About People

*Dustan Kasten, Skookum Digital Works*

Time to first commit is critical.

Don't guess it, test it. If it moves, track it. Get charts in front of people.

-----

## Responsibilities of a Front End Operations Engineer

*Rodney Rehm, Deutsche Telekom*

Know your goals before entering negotiations. Start with something small that has big impact. With finite resources, you have to pick your battles.
