---
layout: post
title: ttt configuration
date: 2010-07-31 13:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- stories
---

## Configuration file for Tic Tac Toe

My next story involves creating some sort of configuration file for my Tic Tac Toe program to centralize data and disable options like 4x4 board if MongoDB is not present.  I have zero experience creating configuration files in Ruby.  I've created config files for other little programs I've built, but they were in XML (yuck).  I asked Micah how I should go about creating one.  He said I can use a simple Ruby file that contains a module with constants.  I took a step further and found this [class](http://mjijackson.com/2010/02/flexible-ruby-config-objects) someone created for creating a config object.  It wraps a hash underneath, and automatically creates methods to access the hash by its keys using dot notation.  I thought that was pretty cool.  I'll see if it'll work for my needs.  I ended up adding several methods to the class to access the hash's keys, values, and index.

## Lunch 'n Learn - Node.js

[Jim Suchy](http://twitter.com/jsuchy) presented his 8LU session on [Node.js](http://nodejs.org/).  It was a good introduction to Node.js, an evented I/O technology for V8 JavaScript.  [V8](http://code.google.com/p/v8/) is Google's fast JavaScript engine, written in C++, currently used in Google Chrome, and Android browser (2.2+).  I didn't quite understand what evented I/O truly meant, but after the session, I had a better idea.  The [slides](http://slideshare.net/simon/evented-io-based-web-servers-explained-using-bunnies) demonstrating bunnies, hamsters, and the squid helped out.  Near the end of the talk, Jim said Node.js might be overkill for some applications which do not have request bottleneck problems.  It's also an overkill to create pure Node.js applications.  He sees Node.js to complement web frameworks like Rails to handle long running processes and such to reduce request time.  Our homework assignment due next Friday is to create a local Node.js server that makes HTTP requests to Flickr, GitHub, Twitter, Facebook, etc.

## Pairing with David

David Putnam came in to the office today for the Lunch 'n Learn and I sat down with him briefly in the afternoon to fix a small RSpec problem he had on his Windows platform.  He also uses IntelliJ for Ruby learning, so I showed him a bit of RSpec stuff I learned from the apprenticeship.  I also gave him some pointers about applying RubyInstaller's DevKit to be able to install certain gems that weren't meant for the Windows platform.  As a person coming from Windows, I know how difficult it can be to set up a Ruby/Rails environment in Windows.  Unix-based users have it so easy!

## The Weekend

I plan to work on the stories assigned in Iteration #5 to play a little catch up game.  Also, from my apprenticeship retrospective, I plan to read chapters from The Well Grounded Rubyist (which should have been completed months ago), and work on a hobby project.
