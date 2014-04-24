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


## Performance and Maintainability with Continuous Experimentation

*Seth Walker, Etsy*

http://sethwalker.me/talks/continuous-experimentation

Measure the growth (in files and loc) of codebase. Growth of codebase decreases confidence of developer and increase need of testing.

### Feature Flags

Configuration driven access to features and library upgrades with staged rollout to users. Internal first, external piece meal.

Supergrep - web-based tool for accessing/reading logs.
Catapult - analytics
Ranger - front-end asset introspection.

Feature flags can lead to bloat/cruft. As experiments are deactivated, it's important to also remove that code.
