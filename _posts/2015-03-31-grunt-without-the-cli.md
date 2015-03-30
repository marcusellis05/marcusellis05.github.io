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

However, if you don't check in those built assets, your back-end devs are going to have a bad time.  They won't be able to run the app locally without running Grunt.  And doing an `npm install` won't install global packages or add them to your path. And the less steps they have to perform, the better.

Further, you might not be able to install global Node modules on your CI server of choice. So being able to run tasks locally would be a good thing.


## A Good Solution

I came up with this little node script that essentially does what the 'grunt-cli' module does.  It requires in the local installation of 'grunt', configures the 'tasks' option and does the Grunt magic.

<script src='https://gist.github.com/marcusellis05/8050184.js'></script>

### Usage

You can save this gist as 'build.js' in the root folder of your project alongside your 'gruntfile.js' and check it into your project. Running it will run the default task alias, 'build'.  If you don't have a 'build' task, you might want to change that in your 'build.js' file.

    $ node build

You can also call any of your other tasks or aliases by passing an additional argument.

    $ node build mochaTest

Or you can call multiple tasks at once.  I'm not sure why you'd want to.  That's what aliases are for, but it is possible.

    $ node build less concat cssmin


## A (Perhaps) Better Solution

I've been pretty enamored of using `npm run` scripts lately. They're stupid simple, and they just seem to work. There's some syntax weirdness that you have to mess with if you want to pass arguments to your run tasks, but you likely don't need it.

If you don't know what `npm run` scripts are, now is a good time to go do some reading up on that: (https://docs.npmjs.com/cli/run-script)[https://docs.npmjs.com/cli/run-script]

So this solution is basically running a simplified, one-liner version of the above script but setting it up in your 'package.json' to make it easier to run. You could also create an `npm run` script that is comprised of multiple `npm run` scripts.

### Usage

In your 'package.json file', add a "scripts" entry:

    {
      "name": "super-awesome-thingy",
      "version": "1.0.0",
      "scripts": {
        "build": "node -e \"require('grunt').tasks(['build']);\""
      }
    }

Then from the command line, you can call that with:

    $ npm run build

But let's say you have multiple tasks to run and you want to start your node app all in one command, you could do something like:

    "scripts": {
      "scripts": "node -e \"require('grunt').tasks(['jshint', 'concat']);\""
      "styles": "node -e \"require('grunt').tasks(['less', 'cssmin']);\""
      "build": "npm run scripts && npm run styles"
      "start": "npm run build && node app.js"
    }

And run that with:

    $ npm run start

Pretty sweet, eh?


## Links

* (http://substack.net/task_automation_with_npm_run)[http://substack.net/task_automation_with_npm_run]
* (http://www.andrewduthie.com/post/running-grunt-tasks-without-grunt-cli)[http://www.andrewduthie.com/post/running-grunt-tasks-without-grunt-cli]
* (https://gist.github.com/marcusellis05/8050184)[https://gist.github.com/marcusellis05/8050184]
