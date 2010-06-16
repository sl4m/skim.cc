---
layout: post
title: day 3 at the 8th light office
date: 2010-06-15 20:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
---

*Note:* Going forward with this post, I will write about the day's apprenticeship experience when I get home from the 8th Light office.

I sat down with Micah today to go over my Tic Tac Toe [program](http://github.com/sl4m/tic_tac_toe_ruby).  He thoroughly gave me advice on how to improve the code, pointing out things I never thought about, and I was able to ask questions about certain things that completely stumped me.  One of the questions was about allowing write access to an instance variable to make it more testable.  Is this ok?  I wanted to prevent 'other people' from accessing it.  Micah came back with a yes and that you should trust your fellow developers.  I never thought about it that way, but it made perfect sense.

I was a bit embarassed when he ran the program and was able to place a mark (e.g., 'X') in a square which already had a mark.  Big Oops.  It goes to show my TDD skill needs improvement.  When I manually tested the program, I did not step outside the boundaries of normal gameplay.  You can tell my exploratory testing brain is a bit rusty.

We went over what [polymorphism](http://en.wikipedia.org/wiki/Polymorphism_in_object-oriented_programming) is and how it plays a role in Ruby and my program.  Unlike other languages where polymorphism requires the use of inheritance and/or interface, Ruby allows polymorphism without it.

"Duck typing is a style of dynamic typing in which an object's current set of methods and properties determines the valid semantics, rather than its inheritance from a particular class or implementation of a specific interface." -- [Wikipedia](http://en.wikipedia.org/wiki/Duck_typing) 

On the whiteboard, we went over the min max algorithm which I still had trouble picturing in my mind.  After Micah carefully showed me examples after examples, it became clear what I needed to do - write a recursive function which builds out the tree and evaluates each node in the tree.  While I haven't had a chance to work on the min max method, I put a lot of time refactoring my program with the help of my fellow apprentice [Li-Hsuan](http://twitter.com/Li_Hsuan). 

I plan to work on extracting the UI code into the UI class and work on the min max method in a new player class, MinMaxPlayer.  Hopefully I will also squeeze some time to read a chapter in [Metaprogramming Ruby](http://pragprog.com/titles/ppmetr/metaprogramming-ruby).  Maybe I'm getting ahead of myself...
