---
layout: post
title: ttt stories and clojure koans
date: 2010-07-28 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- stories
  -- clojure
---

## End of Iteration 4

Unfortunately, I was not able to deliver all stories (again).  I completed the 4x4 Negamax story, but still had a couple of UI stories that I clearly underestimated (in points).  Instead of warning the customer early on, I waited until the last minute which was a big mistake.  I asked Micah when I should warn the customer, and he said immediately when you know.  I think every day during an iteration, I will evaluate the number of points left and determine if I'll be able to complete all stories by the end of iteration.  A simple warning to the customer is better than telling the customer at the last minute.  Bad surprises are the worst thing to bring to the table at the end of iteration meeting.  I've learned my lesson.

With that said, I continued working on the UI story that was supposed to be delivered for Iteration 4.  I've got pretty far ahead and I have a better understanding of how Limelight works.  Now it's a matter of churning through the UI bits to get it completed.  I focused most of my effort today to work on the Options scene.  I showed you yesterday what the new Board scene looks like.  Here is the new Options scene:

![TTT Options Scene New Look](/images/ttt_options_new_look.jpg)

I still need to implement some UI methods to give the user an indication that he/she is clicking on each option.  The following items also still need to be implemented:

* Quit button in Board scene
* Try Again prop with Yes/No child props

I hope to get this completed by early tomorrow and start working on the WEBrick stuff to put my Tic Tac Toe on the web.

## Clojure Koans at Chicago Clojure

Li-Hsuan and I took the train down to attend the Chicago Clojure meetup.  This was my first Chicago Clojure meetup and 8th Light's Colin Jones led the Clojure Koans session for the evening.  I wrote detailed instructions on how-to get started [here](http://skim.la/2010/07/28/clojure-koans-is-awesome).  I really enjoyed learning my first functional programming language.  I recently up an ebook version of Joy in Clojure, but haven't read it yet.  This session was a great kickstart to learning the language.  I highly recommend learning Clojure this way.  It immediately gets you hands-on and you'll soon understand the syntax and language fundamentals.  
