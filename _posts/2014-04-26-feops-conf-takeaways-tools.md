---
layout: post
title: FeOpsConf Takeaways & Tools
published: true
---

Here are my main takeaways from FeOpsConf 2014. I've also aggregated and ctegorized all of the tools that the various speakers mentioned. For some fairly comprehensive notes, check out my [Day 1](/2014/04/24/feops-conf-day-1/) and [Day 2](/2014/04/25/feops-conf-day-2/) notes.

<!--more-->

## Takeaways

#### Lifecycle Logging

One concept that was brought up a few times was "lifecycle logging".  This means making your app rather chatty by default; having loads of log, warn & error statements in the code that explain the state of the app at all times. BazaarVoice ships with this logging in production but it is disabled until a specific cookie is set in the browser.  That way when an issue is reported, it's easy t debug in production and get closer to the root cause.

It seems like a good idea but I'm a little concerned about the extra amount of code and what kind of impact that may have on slower/mobile browsers.

#### Visual Image Diffs

It seemed like every other speaker was talking about visual regression tools. But I also think it would be hard to see through the noise.  Most development is going to cause a change and on purpose.  Image diffs might be a useful tool for QA when doing a full app regression, but I'm a little dubious about how helpful they would be to me as a developer.

#### Web Performance as a Cultural Good

This was the big takeaway for me.  Ensuring that your app is a high level of performance is not the responsibility of any one person or department.  Its not front-end's job nor is it QA's or anyone else's.  It should be a cultural value of the organization.  Everyone should know and care about what the goal is and the entire team should work every day to meet/exceed that goal.


## Tools

#### Automated Browser Testing

* [SauceLabs](https://saucelabs.com/)
* [Testling](https://ci.testling.com/)
* [dalekjs](http://dalekjs.com/)
* [QUnit Extras](https://github.com/jdalton/qunit-extras)
* [Appium](http://appium.io) - mobile test automation framework. Supports real devices, simulators and can test native, hybrid and web apps. Uses native automation capabilities of mobile platforms. Uses a Selenium WebDriver interface to connect to the various automation frameworks.
* [perfjankie](https://github.com/axemclion/perfjankie) - Grunt task to automate testing in browser, save data to CouchDB and generate graphs of metrics over time.
* [phantomas](https://github.com/macbre/phantomas) - easy to install, maintain. It has a grunt plugin.
* [gremlins.js](https://github.com/marmelab/gremlins.js)

#### Visual Regression Tools

* [scylla](http://getscylla.com/) - detect visual changes in a web app.
* [PhantomCSS](https://github.com/Huddle/PhantomCSS)
* [Wraith](https://github.com/BBC-News/wraith)
* [grunt-photobox](https://github.com/stefanjudis/grunt-photoBox)
* [Huxley](https://github.com/facebook/huxley)
* [SiteEffect](http://siteeffect.io) - can determine what changed and what was only shifted as a side effect of that change. Not released yet.

#### Web Application Performance

* [WebPageTest](http://webpagetest.org) - tool for measuring page load and request times with webpage thumbnails.
* [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) - best practices for desktop and mobile.
* [Boomerang](http://yahoo.github.io/boomerang/doc/) - measure webpage performance on client and report back to server.
* [chrome-ops](http://github.com/jlipps/chrome-ops) - Node.js helper library for dealing with Chromedriver performance logs
* [browser-perf](https://github.com/axemclion/browser-perf) - record actions, measure with probes and aggregate with metrics
* [SpeedCurve](http://speedcurve.com/) - dashboard tool for displaying front-end performance metrics.

#### Styleguides and Documentation

* [Rizzo](http://rizzo.lonelyplanet.com/styleguide/) - Lonely Planet's styleguide.
* [Source](http://sourcejs.com) is a front-end documentation engine.

#### CSS Testing & Optimization

* [csste.st](http://csste.st) - collection of current techniques and tools available for CSS testing
* [ucss](https://github.com/operasoftware/ucss)
* [uncss](https://github.com/giakki/uncss)
* [dom-prof](https://github.com/josh/dom-prof) - phantomjs crawler
* [DOM Monster](http://mir.aculo.us/dom-monster/) - bookmarklet
* [hardy.io](http://hardy.io) - based on selenium, uses gherkin syntax, checks copmuted style.

#### Translations

* [Transifex](https://www.transifex.com/) - SaaS translation provider
* [grunt-i18n-abide](https://github.com/mozilla/grunt-i18n-abide) - Grunt task for build translations
* [R2](https://github.com/ded/R2) - library to automatically switch styles from LTR to RTL
* [moment.js](http://momentjs.com/) - really good language support

#### Code Coverage

* [istanbul](https://github.com/gotwarlost/istanbul)
* [coveralls](http://coveralls.io)

#### Miscellaneous

* [Feature flags](https://github.com/etsy/feature) - Configuration driven access to features and library upgrades with staged rollout to users. Internal first, external piece meal.
* [Supergrep](https://github.com/etsy/supergrep) - web-based tool for accessing/reading logs.
* [node-jscs](https://github.com/mdevils/node-jscs) - Code style checker
* [git-ci-hooks](http://bit.do/git-ci)
* [Git Tutorials](http://atlassian.com/git)
* [Perspective](http://pixxa.com/) - presentation tool for displaying charts
