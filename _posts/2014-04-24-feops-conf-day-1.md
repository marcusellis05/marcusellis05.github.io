---
layout: post
title: FeOpsConf Day 1
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

http://sethwalker.me/talks/continuous-experimentation

Measure the growth (in files and loc) of codebase. Growth of codebase decreases confidence of developer and increase need of testing.

### Feature Flags

https://github.com/etsy/feature

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
