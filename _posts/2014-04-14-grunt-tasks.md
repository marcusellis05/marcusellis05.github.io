---
layout: post
title: Grunt Tasks
---
Introducing [grunt-tasks](http://marcusellis05.github.io/grunt-tasks/).

## The Problem

A decent Gruntfile can quickly grow to an unmanageable length.  If you are building multiple versions of your application for different devices, or if you have environment specific build steps, a 400+ line Gruntfile is not out of the realm of possibility.

<!--more-->

I ran into this issue at work.  I've created a project scaffold using Node, Backbone, Require.js, Handlebars, Less, and several other libraries.  So there's lots of compilation, optimization, concatenation, etc.  With build profiles for desktop, mobile and print, the Gruntfile for that scaffold was over 430 lines with appropriate comments and whitespace.  It got kinda difficult to maintain.  So, I decided to fix that.

## The Solution

My idea to solve this problem was to put related tasks into individual files and place those files in a specific folder.  If my solution was going to be useful to anyone else, it needed to be configurable.  I figured I should use the [globule](https://www.npmjs.org/package/globule) module to make it easier to configure which files to use and I was already using [load-grunt-tasks](https://www.npmjs.org/package/load-grunt-tasks) to automatically load Grunt plugins so I figured I should bake that in too.

It does a "pseudo-merge" of the task definitions in those files. The merge isn't recursive.  It's built to let you have the same plugin configured in 2 different files.  For example, you could have a "concat:css" task defined in one file and a "concat:js" task in another.  As long as the "subtask" name is different, there won't be a collision and both will be callable.

Anyhow, I think it's a pretty simple yet elegant solution. It's got decent documentation, so I won't cover all the configuration options.  There's also a good [example setup](https://github.com/marcusellis05/grunt-tasks/tree/master/example) in the Github project, so check that out if this post made no sense.

If you like this idea but are looking for a more robust solution, you may be interested in [PintJS](http://www.pintjs.com).  It more or less wraps Grunt, and it allows you to modularize your code and run tasks concurrently.

## Ideas? Issues?

I don't have too many plans for this module beyond what it is now.  The only thing I can think to add is to have it accept JSON files in addition to JS files.  I'll be adding that sooner or later.  But probably not sooner.

It should probably have unit tests because reasons.

If you run into any issues or have an idea to improve it, please create an issue against the [Github project](https://github.com/marcusellis05/grunt-tasks/issues).
