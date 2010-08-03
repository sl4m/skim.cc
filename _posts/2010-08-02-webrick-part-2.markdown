---
layout: post
title: webrick - part 2
date: 2010-08-02 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- stories
  -- webrick  
---

Today I researched some more on WEBrick, learning about servlets, get/post, response/request, and ERB.  I was able to get a simple home page going for my Tic Tac Toe program.  Similar to the other UIs I've worked on, this WEBrick version will also make sure MongoDB is properly installed before enabling the 4x4 option.  The select inputs are retrieving their "options" from the config.rb I created for a recent story.  Here is what I have so far.

![TTT WEBrick Options Draft](/images/ttt_webrick_options_draft.jpg)

The only problem I'm facing now is figuring out how to test WEBrick.  I dug some info and found out [Sermoa](http://twitter.com/sermoa) created a wiki called [licky](http://github.com/sermoa/licky) and created her own testing framework.  I'll probably end up using net/http library inspired from her project.

Tomorrow, I plan to work on the story which calls for displaying the Tic Tac Toe board on WEBrick and start by creating tests first.
