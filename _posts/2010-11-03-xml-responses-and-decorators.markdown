---
layout: post
title: xml responses and decorators
date: 2010-11-03 19:00:00 -05:00
categories:
  -- client
  -- ruby
  -- rails
  -- xml
---

Today, I spent the day pairing with Eric Smith, attempting to grasp the context of the problem he was working on.  Basically, the story asked for generating response xmls for every set of answers to survey questions.  Some questions have follow\-up questions which also need to be in the response xml.  At first, I had a bit of trouble understanding the context of the problem, but later understood the basics and tried the best I could to be a really good rubber ducky, a spell checker, and bouncing ideas around.  I hope I did not slow him down.

When working with pairs, I always try to observe the other person's workflow.  Specifically during the session, I try to learn about the way the person writes tests, the tools that were used, the diagrams on the whiteboard, the breaks in between coding, etc.  Eric is a VIM power user and he knows his TDD, so I was able to pick up on a few VIM commands here and there, learn a bit of Rails DSL, and RSpec tricks:

* *:null\_object* on a mock object basically says any method called on the mock object will not throw an error.
* using *anything* in the argument allows any parameter to be passed in
* *be\_blank* is only available in Rails, but allows you to test values that are blank (instead of using \== "")

I was happy to see the way I usually write RSpec tests are somewhat similar to the way Eric writes his.  He liked spiking code to understand the context of the problem and wrote tests for the particular area we were working on.  At the end of the day, we did not finish the story, but I hope I had contributed to the story, rather than be a hindrance.  

Tomorrow, I'll be on site with Jim and the Erics and I will continue working with them to help with stories, on call tech support, etc.
