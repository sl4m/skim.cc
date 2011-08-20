---
layout: post
title: rails and effective study habits
date: 2010-09-12 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- tic tac toe
  -- rails
  -- continuous learning
---

## Rails 3

Last Friday, I was having some trouble figuring out how to add the Tic Tac Toe game engine library into my Rails 3 project without duplicating the files.  A couple of ideas came to mind.  I can create a symlink and point it to the game engine folder.  Another idea was to create a local gem and create a rake task that vendors the game engine when running the Rails application.  That way, it can have the latest version of the game engine library.  I went for the latter as I didn't think symlink would work, so I started researching on how to create a gem.

I looked at one particular gem project, [Specjour](http://github.com/sandro/specjour/), to see how [Sandro](http://twitter.com/sandrot) created the gem folder structure layout.  He uses a Ruby gem called [jeweler](http://github.com/technicalpickles/jeweler), which is used to create and manage gems.  It seemed like an easy way to create a gem.  There's a bin folder which contains a file named after the gem and includes the command line options.  I'm sure I'm missing the intricate details, but for the most part, everything else looks the same as my game engine library.  The only thing I'll have to do is create a namespace for the game engine and include all classes under the new namespace.  This shouldn't hard to do, as [I've done it before](http://skim.cc/2010/08/23/rails-and-refactoring/) in a Rails project.

With regards to session handling, which I'll need for multiplayer support, it looks like I'll need to read up on Action Dispatch.  This is a new component in Action Pack in Rails 3 that handles the following:

* Request handling and parameter parsing
* Sessions, Rails' flash, and cookie storage
* File uploads
* Routing, URL matching, and rescuing errors
* HTTP conditional GETs
* Client response and HTTP status code

Taken from [Rails 3 Upgrade Handbook](http://www.railsupgradehandbook.com/)

I will into these in more depth tomorrow.

## Effective Study Habits

I read an article on the [New York Times](http://nyti.ms/9qZDs7) referenced by [Mark Needham](http://www.markhneedham.com/blog/2010/09/12/learning-study-habits/) and [Michael Feathers](http://twitter.com/mfeathers/status/24215110861) that talks about the common wisdom about good study habits and how they contradict with new, simple techniques.  Here are some quotes that I find interesting:

> Varying the type of material studied in a single sitting - alternating, for example, among vocabulary, reading and speaking in a new language - seems to leave a deeper impression on the brain than does concentrating on just one skill at a time. Musicians have known this for years, and their practice sessions often include a mix of scales, musical pieces and rhythmic work. Many athletes, too, routinely mix their workouts with strength, speed and skill drills.

I always thought my inability to study a single piece of material in a single sitting was a flaw in my study habits.  Like Mark, I can't sit down and study something for more than a couple of hours.  I think my mind wants to wander and study something else on my long list of interesting topics.

> "The idea is that forgetting is the friend of learning," said Dr. Kornell. "When you forget something, it allows you to relearn, and do so effectively, the next time you see it."

> It may be that the brain, when it revisits material at a later time, has to relearn some of what it has absorbed before adding new stuff - and that that process is itself self-reinforcing.

> The harder it is to remember something, the harder it is to later forget. This effect, which researchers call "desirable difficulty," is evident in daily life.

So when you forget something you've learned, you're essentially creating a "desirable difficulty."  When you relearn the material, it will be more difficult to forget.  I wonder how pomodoros and varying materials per session can help absorb more of the material.
