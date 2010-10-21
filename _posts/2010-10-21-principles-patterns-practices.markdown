---
layout: post
title: principles, patterns, and practices
date: 2010-10-21 10:00:00 -05:00
categories:
  -- design patterns
  -- solid
  -- principles
  -- patterns
  -- practices
  -- software design
---

I picked up the Agile Software Development - Principles, Patterns, and Practices (otherwise known as PPP) book again.  It made for good use when learning about the five patterns.  I regret not reading this book earlier.  Colin wrote in his blog how he could have taken advantage of some of the refactorings for his Tic Tac Toe Java implementation after reading the Refactoring book.  I feel the PPP book could have helped me not only with refactoring, but with pattern usage, avoiding SOLID principle violations and with the Bowling Kata.  But at the same time, after getting comfortable in Java, the PPP book seems easier to read.  I can understand and read the code.

### Bowling Game with the Bobs

I really enjoyed reading the dialogue between the two Bobs tackling the bowling problem.  They started off with a simple UML design on a napkin that had three classes: Game, Frame, Throw.  In the end, there were two, of which one were not in the original design: Game and Scorer.  Scorer was created to remove an SRP violation in the Game class.  What I found interesting was the consistent refactorings throughout the session, the simplicity of the design, and scratching their own itch when it came to code smells.  The resulting code works, can easily be changed (easy to add new functionality), and is readable - the three functions every software module should have.

Here are some notes during their session:

* After creating the simple UML diagram, they started at the end of the dependency chain and worked backwards
* They moved up the dependency chain until they were working on an object that had more than just getter/setter methods
* They pointed out uglies without hesitation
* They asked if this Bowling module will be used by thousands of people other just them when adding conditions to protect user
* They pointed out things they didn't like without hesitation
* They avoided circular references
* They wanted their tests to reveal design (e.g., introducing LinkedList for Frames)
* They avoided code that did not make sense or was not readable (e.g., Magic Number 21)
* They changed the method names numerous times
* They avoided writing code that could have different results when using different compilers (e.g., order dependency)
* They removed tests that were not useful
* At the end, most of the methods contained one line of code

### What is Software Design?

One part in Uncle Bob's book talked about Jack Reeves' [article](http://www.developerdotstar.com/mag/articles/reeves_design.html) titled, "What is Software Design?"  In it, Reeves describes how source code is the documentation for software.  He compares and contrasts hardware design and software design, hardware engineering and software engineering.  Programming, testing, and debugging are all part of software design activities and should not be shortchanged.  He believes software development should not mimic engineering as it's more of a craft.  Unlike hardware engineering, the software development cycle does not have a step where the "designers" hand off the design to the manufacturers where they go ahead and create the product from the design.  The designers create the product at the same time as creating the design.

I [tweeted](http://twitter.com/#!/skim/status/27999732472) yesterday about wanting to read Jack Reeves' afterword to his afterword to his afterword to his article if he should ever write one.  I want to know if functional languages is considered an advance in programming in his POV and if auxilliary documentation still needs more emphasis.

Well that's I have so far.  I'll write more when I make progress in the PPP book.
