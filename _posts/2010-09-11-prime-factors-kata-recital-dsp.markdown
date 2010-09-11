---
layout: post
title: prime factors kata recital, dsp
date: 2010-09-11 10:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- tic tac toe
  -- webrick
  -- kata
  -- digital signal processing
---

## Prime Factors Kata and DSP Session

I was the opening band for today's Lunch 'n Learn, right before Doug presented his first session in Digital Signal Processing.  I didn't talk during the kata which Micah pointed out at the end.  It wasn't necessarily a bad thing; he mentioned other people like to talk while they walkthrough, while others play music.  I chose the third option.  Anyway, I started off on the right foot, showing off the cool keyboard shortcuts on RubyMine, but on the test, "it factors 9", I missed a crucial step and had a test hanging for a while.  It wasn't suppose to hang.  A couple of people were hinting that I was missing something and I was able to quickly recover.  It's funny, you practice so many times alone, but when you're performing in front a live audience, there are chances you can choke.  And I choked.  It was fun though.  I received several compliments and I felt pretty good about towards the end.

We went right into Doug's session on DSP.  He began with the basics: what is sound? sample rate? bits?  It was an interesting topic for me since I'm interested programming in audio (e.g., Max/MSP) and have some experience recording live music with a DAT recorder.  Our homework is to write an audio filter similar to what karaoke machines do to filter out the vocals.  He gave us a sample [XCode project](http://github.com/dougbradbury/8LU-DSP) and told us we should not have to write more than one line of code.  I'm not sure what that means right now.  I'll have to take a look at the code in depth (C++) to figure out what he's talking about.

## Putting WEBrick TTT to the Test

I started up my WEBrick version of Tic Tac Toe and asked Brian to try out the game, while I also played several games.  It worked without problems except Brian found a bug where clicking the empty spaces after the game was over, it displayed "Internal Error".  I looked into the issue and it's the fact that the rhtml when converted tries to use the current player's piece.  Since the current player was not being set it was trying to access the piece attribute on a nil object.  I fixed the problem and added a test to make sure this problem won't happen again.

I'll be focusing on the Rails 3 version of Tic Tac Toe this weekend.  I'm reading the [edge version of the Rails Guide](http://edgeguides.rubyonrails.org/) to guide me along the way.
