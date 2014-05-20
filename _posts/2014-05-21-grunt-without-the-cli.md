---
layout: post
title: Grunt without the CLI
published: true
---

Grunt is great.  But global modules are not.  Especially when working in a team.

<!--more-->

## The Scenario

Let's say you have a team of back-end and front-end developers and you use Grunt for your app to concatenate files, precompile templates and/or compile Less/SASS to CSS.

If you're a front-end dev, it's no big deal.  It's reasonable to require that you install the 'grunt-cli' module globally because you're going to be using it a lot.

However, if you don't check in those built assets, your back-end devs are going to have a bad time.  They won't be able to run the app locally without running Grunt.  And doing an `npm install` won't install global packages or add them to your path.

Further, your CI server of choice probably won't be able to run your Grunt tasks.

## The Solution

I came up with this little node script that essentially does what the 'grunt-cli' module does.  It requires in the local installation of 'grunt', configures the 'tasks' option and does the Grunt magic.

<script src='https://gist.github.com/marcusellis05/8050184.js'></script>

## Usage

You can save this gist as 'build.js' in the root folder of your project alongside your 'gruntfile.js' and check it into your project. Running it will run the default task alias, 'build'.  If you don't have a 'build' task, you might want to change that in your 'build.js' file.

    $ node build

You can also call any of your other tasks or aliases by passing an additional argument.

    $ node build mochaTest

Or you can call multiple tasks at once.  I'm not sure why you'd want to.  That's what aliases are for, but it is possible.

    $ node build less concat cssmin