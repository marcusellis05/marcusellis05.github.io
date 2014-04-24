---
layout: post
title: FeOpsConf Notes, Day 1
published: true
---

## Keynote

*Alex Sexton, Stripe*

What is Front End Ops? Serving web pages/apps is super hard.  FeOps is the collection of things you can do to make serving them easier.  The act of building performance (and dev happiness) in as a default.

Why? So you can focus on your product.  Mature FeOps benefits the developer.

Speed is the metric we measure by.  Speed of app, speed of ???, speed of development.

### Speed of the app

How to speed up your app in 5 simple steps.

1. Forget everything you know b/c it's wrong.
2. It's probably the network.
3. Read "High Performance Browser Networking".
4. Measure.
5. Measure.

Measure distribution of load times, not just the aggregate. Break it down by network speed, geography, device, etc. Meaure twice. Optimize once.

### Build a Dashboard

Measure performance and tie to commits.

* Speed index over time
* Page weight over time
* Build time over time

[SpeedCurve](http://speedcurve.com/) - dashboard tool for displaying front-end performance metrics.

### Other Thoughts

* Never do anything twice. AKA Cache everything.
* Implement lifecycle logging.  Optional console logging.
* Update your dependencies every week.
* Have a rigorous styleguide and automated linting.

------

## Performance and Maintainability with Continuous Experimentation

*Seth Walker, Etsy*

[Slides](http://sethwalker.me/talks/continuous-experimentation)

Measure the growth (in files and loc) of codebase. Growth of codebase decreases confidence of developer and increase need of testing.

### Feature Flags

[https://github.com/etsy/feature](https://github.com/etsy/feature)

Configuration driven access to features and library upgrades with staged rollout to users. Internal first, external piece meal.

* [Supergrep](https://github.com/etsy/supergrep) - web-based tool for accessing/reading logs.
* Catapult - analytics
* Ranger by Etsy (closed source) - front-end asset introspection.

Feature flags can lead to bloat/cruft. As experiments are deactivated, it's important to also remove that code.

Etsy deploys application code 50 times per day.

------

## Git, CI and Making it Pretty

*Sarah Goff-Dupont, Atlassian*

### CI & Branching

Everything is in a branch (bugs, features, etc.).  Master is always pristine and releasable. Run CI on branches so you can ensure Master never gets polluted. Do so by cloning Master's CI config. You can use a git hook to detect new branches and automatically do the clone for you. There is a Jenkins plugin; it's built into Bamboo.

Building with every commit can lead to lengthy build queues. Make branch builds a manual, push-button build; master and release branches stay automatic. The only commits to master and release branches should be merges from feature and bug-fix branches. Bamboo can automatically disable/delete unsused branch build configs.

Rebase before merging. Or run an integration branch (is that the same as "Staging"?).

### git hooks

Scripts that are run when something happens in your branch. Can run client- or server-side as well as pre- or post-activity (ie, before or after a commit or push). Examples: Run jshint client-side before allowing a commit; check for proper test coverage before allowing a merge.

### Tools

* [git-ci-hooks](http://bit.do/git-ci)
* [Git Tutorials](http://atlassian.com/git)

------

## Rebooting Flickr on a Node.js Stack, One Page at a Time

*Bertrand Fan, Flickr*

Flickr is currently built with PHP, transitioning to Node.js. They are using Express. The reboot stack sits between the web client and the API.

In production they're running on Manhattan (sorta like Heroku). 1 Manhattan instance is 1 server running 16-32 Node processes.

They developed a way to bucket users and route them to the new, reboot stack while leaving others on the classic, PHP version of the app.

Apache Traffic Server and cookies to handle routing to classic vs reboot.

UglifyJs can do conditional compilation by evaluating global variables.

------

## The Glitch in the Game

*Sebastian Golash, Deuthce Telekom*

[http://dalekjs.com/](http://dalekjs.com/)

### Image Regression

The art of knowing which pixels are allowed to change between builds. Image based diffs. Can be noisy and is difficult to determine the cause of the change.

**Tools**

* wraith
* grunt-photobox
* siteeffect.io - can determine what changed and what was only shifted as a side effect of that change. Not released yet.

### Performance Regression

The art of knowing how changes are allowed to affect performance.

You can use HAR files to capture an archive of network performance.

But loading is only one piece. Layout and scroll performance matter.

**Tools**

* phantom?s - easy to install, maintain. It has a grunt plugin.
* Chrome Telemetry - Python framework that collects a lot of data tha a browser generates. It's hard to setup. Topcaot uses it.

### Monkey Testing

Automated UI testing to try to break the app and discover odd conditions taht produce errors.  See the monkey theorem.

**Tools**

* Gremlins.js

### CSS Regression Testing

The art of testing the cascade.  CSS is declarative language so it must be tested differently. Checking the output is not pure CSS testing.

**Tools**

* csste.st - collection of current techniques and tools available for CSS testing
* hardy.io - based on selenium, uses gherkin syntax, checks copmuted style.

------

## Fearless Browser Test Automation

*John David, Dalton, Microsoft*

Manual testing is craxy hard. Lots of browsers, variations, versions, etc.

Browser Test Automation Options:

* Sauce Labs
* Testling

Make the CI server do everything.

Lodash uses Travis CI, SauceLabs, coveralls.io, Istanbul, QUnit, QUnit Extras.

**npm deps**

* chalk
* ecstatic
* request
* sauce-tunnel(-sc3-1)

** The cool**

* IE compat mode
* Concurrent tunnels
* Automatic retries
* Tailored platforms
* QUnit extras

------

## Performance Testing for Android Web Apps

*Jonathan Lipps, SauceLabs*

[Appium](http://appium.io) is a mobile test automation framework. Supports real devices, simulators and can test native, hybrid and web apps. Uses native automation capabilities of mobile platforms. Uses a Selenium WebDriver interface to connect to the various automation frameworks. Can be installed and run with:

    npm install -g appium && appium

[http://github.com/jlipps/chrome-ops](http://github.com/jlipps/chrome-ops)

Automated testing prevents...

* Regressions in functionality
* Regressions in performance

Automated testing provides...

* Explicit specification of functionality
* Explicit specification of performance

You can use appium with Sauce Labs.

------

## Taking Development Tools to the Next Level

*Robert Haritonov, OK.ru*



------

## Adding Rendering Metrics to Browser Performance Lab

*Parashuram Narasimhan, Microsoft*

------

## Customers Love the Product, Let's Keep it that Way!

*Dusty Jewett, Simply Measured*

------

## Web Performance Engineers - The Hunt for the Mythical Beast

*Tobias Baldauf, Akamai*
