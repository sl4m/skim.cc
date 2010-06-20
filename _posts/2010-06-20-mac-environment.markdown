---
layout: post
title: mac environment
date: 2010-06-20 17:00:00 -05:00
categories:
  -- software craftsmanship
  -- mac
---

Over the weekend, I spent some time setting up my development environment on a newly acquired MacBook Pro.  The past two weeks, I was using my first generation Core 2 Duo MacBook and everything I did on it, development wise, had the fan constantly spinning.  When I used the same set of commands on this MBP, it churned right along in silence.  I love it.  I used some parts of thoughtbot's [2009 Rubyist Guide to a Mac OS X development environment](http://robots.thoughtbot.com/post/159805668/2009-rubyists-guide-to-a-mac-os-x-development) for my MacBook and I ended up using it again for the MBP.

On my newly installed Snow Leopard, I installed the following applications:

* [XCode](http://developer.apple.com/technologies/xcode.html) (recommended to download from Apple site)
* [Git for OSX](http://code.google.com/p/git-osx-installer/)
* [MacVim](http://code.google.com/p/macvim/) (built from wiki [instructions](http://code.google.com/p/macvim/wiki/Building))
* [IntelliJ](http://www.jetbrains.com/idea/)
* [Quicksilver](http://www.blacktree.com/) (latest ß58 beta from GitHub [repo](http://github.com/tiennou/blacktree-alchemy/downloads))
* [homebrew](http://github.com/mxcl/homebrew) (replaces MacPorts, need to be built)

There are two important config file repos that I use.  [One](http://github.com/jferris/config_files) is from thoughtbot's Joe Ferris for configuring aliases, irb, gem, git, zsh, vim, etc.  The [other](http://github.com/akitaonrails/vimfiles) is from Fabio Kung (aka AkitaOnRails) who maintains a really nice configuration for vim.  I replaced Joe's vim configuration for Fabio's.  I'm also using [zsh](http://en.wikipedia.org/wiki/Z_shell) instead of [bash](http://en.wikipedia.org/wiki/Bash), just to try it out.  So far I'm pleased with it.

The ruby gems I quickly installed were:

* rvm (ruby version manager)
* jekyll (to write this blog post)
* rspec (to test my Tic Tac Toe program)

I'm not developing in Rails yet, so I'll install the environment later.  The following is optional, but I also built:

* [node.js](http://github.com/ry/node) (evented I/O for v8 JavaScript)
* [ClojureX](http://github.com/citizen428/ClojureX) (for some clojure fun)

I haven't started reading any of the Ruby books I wanted to read due to the errands I needed to run.  Plus my car brakes completely died (leaking line) and I can't get it serviced until Monday.  My [NAS](http://en.wikipedia.org/wiki/Network-attached_storage) power supply died.  I called the manufacturer to order a replacement part.  Verizon Wireless service is pretty sketchy in my area, so I ordered a network extender.  They gave me a great deal, so kudos to Verizon.  Everything systematically failed this weekend.  Hopefully there won't be problems like this next weekend.
