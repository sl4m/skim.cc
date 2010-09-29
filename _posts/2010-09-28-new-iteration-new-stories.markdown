---
layout: post
title: new iteration, new stories
date: 2010-09-28 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- yak shaving
  -- java
  -- stories
---

## End of Iteration Meeting

Micah and I had our end of iteration meeting.  I'm happy to say I've completed all stories for this iteration with one minor exception: I still need to complete the Tic Tac Toe Rails 3 app.  It was marked as zero points since it's unfair to bill the customer when it was clearly my mishap.  So I will work on it this iteration.  Also, I mentioned in my previous post, I forgot to support comments in the Limelight styles.rb converter, so I'll have to handle that as well.  I demoed the other stories to Micah and he seemed happy with all of them.  As I get in the habit of thinking in story points, my story estimates and completion should improve.

## Iteration #11 Stories

Here's what in store for Iteration #11:

* Fix a generator bug in statemachine gem
* Write FitNesse/slim tests for the styles.rb translator
* Write a Tic Tac Toe implementation in Java

The last two will be the most challenging for this iteration.  I don't think the Tic Tac Toe story will be too challenging as I've written it already in two other languages, rather it will just take a bit more time writing in Java.  I think I'm more comfortable writing in Java, but there are some things that force me to look in the Java API docs.

## Pull Request for statemachine gem

Later in the day, I actually fixed the generator bug in the statemachine gem and sent Micah a pull request.  It was a rather easy fix.  You can see the pull request [here](http://github.com/slagyr/statemachine/pull/3).

## Comment Support for Limelight styles.rb converter

This feature is difficult to implement than I previously thought.  Since the styles.rb file is being read byte by byte, it needs to know when it enters the comment state.  Once it finds the \# (Ruby's comment), it'll need to skip all characters before the new line.  I'm not sure whether or not to use [superstates](http://slagyr.github.com/statemachine/example4.html) with history state or if I get away with just adding more transitions.  Regardless, I'll need to keep track of when the fileInputStream goes into comment mode and when it leaves comment mode (upon detecting new line).  I'll look into this more tomorrow.
