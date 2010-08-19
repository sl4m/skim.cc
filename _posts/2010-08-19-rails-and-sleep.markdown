---
layout: post
title: rails and sleep
date: 2010-08-19 09:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
---

My, my, a 15 minute cat nap turned into a full fledged sleep thanks to my Android timer *not going off*.  I had planned to work on the Node.js homework, but it looks like I'll be working on it tonight.

Yesterday, Matt and I continued working on the Rails project.  We actually finished the implementation by the end of the day, working through some spiking to see the working solution.  Many thanks to [Craig](http://twitter.com/demmer12) for being super helpful and knowledgeable.  We asked him many questions and he was very detailed in his answers.

I'm learning so much on Rails, I have an itch to continue to learn more.  I'm really glad to have learned how to use Limelight because it shares similar conventions with Rails and I'm glad to have learned how to work with WEBrick because it's as low level as you can get when developing the web - talking directly to the web server and have it serve your pages.

Today, we will work on another task similar to the last one.  I look forward to the challenges and the learning.  

## Reading

On Tuesday night, I began reading parts of the Design Patterns in Ruby and came across Russ Olsen's ideas on the set of meta-design patterns:

* Separate out the things that change from those that stay the same.
* Program to an interface, not an implementation.
* Prefer composition over inheritance.
* Delegate, delegate, delegate
* You ain't gonna need it

The first one sounds like the layman's terms for saying manage your dependencies, understand the symptoms of rotting design, and apply the SOLID principles.

Program to an interface, not an implementation is Dependency Inversion principle which says to "depend on abstractions, not on concretions."

I knew about composition and applied it to my Tic Tac Toe project, but did not know it was the word to describe it.  Delegation is something new to me.  I didn't know this was allowed per se.  It's where you have one class, say Car and an Engine class.  You create an instance of the Engine class inside the Car class and the methods start\_engine and stop\_engine simply call the Engine instance's methods.

From delegation, I read about [Law of Demeter](http://en.wikipedia.org/wiki/Law_of_Demeter) which Craig threw out yesterday in one of our conversations.  Then I quickly [read about the Presenter pattern](http://blog.jayfields.com/2007/02/ruby-forwardable-addition.html) which uses [Forwardable](http://ruby-doc.org/stdlib/libdoc/forwardable/rdoc/index.html) to delegate and not violate the Law of Demeter.

I plan to go back to my Tic Tac Toe project and apply these design patterns.
