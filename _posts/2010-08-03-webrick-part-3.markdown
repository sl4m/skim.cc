---
layout: post
title: webrick - part 3
date: 2010-08-02 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- stories
  -- webrick  
---

I worked on my last two stories for this iteration, polishing one, and creating tests/code for the other.  I'm a little worried my code is becoming more smelly as more features are being added to the project.  Currently, all three UIs (console, Limelight, WEBrick) are in the same project.  All specs live in the same spec folder, all console and shared classes live in the same lib folder, and Limelight is structured in its own unique way.  This next iteration I plan to have a better layout of my source and tests.

Another thing I'm noticing is that there are some shared methods that need to be extracted and put into a shared library.  I'm having a problem naming the class/module that would best fit the collection of these shared methods.  Hopefully Micah can shed some light on this.

Colin gave some pointers how to test ERB stuff.  I ended up extracting a heredoc string and putting it into its own file.  Plus Ruby code in the ERB heredoc string has been extracted into its own methods so I can test them easily.  

I'm constantly reading [Gnome's Guide to WEBrick](http://microjet.ath.cx/webrickguide/html/html_webrick.html) to understand WEBrick a bit more and it's actually a great guide to learn about WEBrick.  Most of the content is making sense to me now and I think I have a good understanding on how things work in WEBrick.  One thing I'll need to figure out is how to have a hyperlink mimick a human player move on the Tic Tac Toe.  I've been playing with the idea of using query strings in the URL or somehow tagging value to a particular link clicked inside a Tic Tac Toe square.  I'll need to do some more research.


