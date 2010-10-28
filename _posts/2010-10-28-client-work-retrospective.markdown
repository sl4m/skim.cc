---
layout: post
title: client work retrospective
date: 2010-10-28 19:00:00 -05:00
categories:
  -- client
  -- ruby
  -- eventmachine
  -- retrospective
---

Today is my last day working with Doug and Li\-Hsuan.  In case you haven't noticed, I'm on my apprenticeship tour where I tour around each client project, helping out the 8th Lighters, learning about the project, "stand\-in" for stand up meetings, and experience real world scenarios.  I really enjoyed working with them and look forward to working them in the future.

### Ruby Gem Creation

While this was a small task, I didn't know how to create a Ruby gem before.  Fortunately, Doug already had the library ready to go by encapsulating the library in a module (not sure if there is a name for this convention).  I just needed to use [Jeweler](http://github.com/technicalpickles/jeweler) and it created the Gemspec for me.  Doug simply upped the version and recreated the gem when pulling in changes.  It worked out well.

### EventMachine

I was pretty much using EventMachine the entire time I was on the project.  Li\-Hsuan and I kept adding features as Doug asked for them.  We added features like multiple callback and errback handling and learning a ton about EventMachine during the process.  Testing EventMachine was a bit of a headache.  I can't tell if the tests were not designed properly or if it was the fact that EventMachine was sometimes difficult to understand, but we were able to test everything we've implemented.  I'd sometimes forget how certain features worked in the library and had to read the code again to understand what was going on.  Also, I don't know how many times we put *puts* or *p* statements in the code and tests to figure out what was going on.  Again, I'm not sure if it's a result of code smells or something else.

### Client Communication

While our stand up meetings were short, it was nice to introduce myself to the customer and talk to them briefly about the features we've implemented.  For the past eight years as a software tester, I've never actually talked to a customer.  My connection with the customer were business analysts, developers and perhaps the QA manager.  So working with the client this week shined a different kind of light.  By removing the middle persons in between you and the client, you can provide personal service to the client and have better communication.  This is also my first time working in an agile environment, so the the frequent feedback (e.g., daily stand ups) help bridge the communication between us and the client.

### Touring Continues

Starting tomorrow, I will be working with other 8th Lighters on a different project.  I look forward to learning a lot and getting my hands dirty.  It's going to be fun.
