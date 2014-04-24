---
layout: post
title: FeOpsConf Day 1
published: true
---

## Keynote

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

Measure distribution of load times, not just the aggregate. Break it down by network speed, geography, device, etc.

> Meaure twice. Optimize once.

### Build a Dashboard

Measure performance and tie to commits.

* Speed index over time
* Page weight over time
* Build time over time

[SpeedCurve](http://speedcurve.com/) - dashboard tool for displaying

### Other Thoughts

* Never do anything twice. AKA Cache everything.
* Implement lifecycle logging.  Optional console logging.
* Update your dependencies every week.
* Have a rigorous styleguide and automated linting.
