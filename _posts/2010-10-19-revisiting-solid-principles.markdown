---
layout: post
title: revisiting solid principles
date: 2010-10-19 09:30:00 -05:00
categories:
  -- design patterns
  -- tic tac toe
  -- solid
  -- uml
---

## Design Patterns

According to Gamma in the book, Design Patterns: Elements of Reusable Object-Oriented Software, in order for a solution to qualify as a pattern, it must be used in at least three unrelated projects.  This was called the "rule of three."  Design Patterns are important, not only for their solutions to problems, but for their high-level names that can be used as vocabulary for communication.  Identifying design patterns and knowing which one to use is just as important as other any other development practice.  

Design patterns and SOLID principles complement each other.  The patterns help prevent violating SOLID principles and help create a solution to a problem in context (James O. Coplien).

Micah and I went over the SOLID principles yesterday using my Tic Tac Toe Java implementation as an example.  We identified my design violated the following:

* [OCP](http://en.wikipedia.org/wiki/Single_responsibility_principle)
* [LSP](http://en.wikipedia.org/wiki/Liskov_substitution_principle)
* [DIP](http://en.wikipedia.org/wiki/Dependency_inversion_principle)
* [ISP](http://en.wikipedia.org/wiki/Interface_segregation_principle)

When violating one principle, sometimes it violates another.  For example, when violating DIP, in order to fix DIP, you violate OCP.  Micah asked me to draw a UML class diagram that shows a Tic Tac Toe design that does not violate any SOLID principles.  He also gave me a list of patterns to look up and see if it can be used for the design:

* [Abstract Server](http://today.java.net/pub/a/today/2004/06/8/patterns.html)
* [Abstract Factory](http://en.wikipedia.org/wiki/Abstract_factory_pattern)
* [Observer](http://en.wikipedia.org/wiki/Observer_pattern)
* [Strategy](http://en.wikipedia.org/wiki/Strategy_pattern)
* [Template Method](http://en.wikipedia.org/wiki/Template_method_pattern)

I will be presenting the new UML diagram and explain the five patterns later today.  I will describe them in detail in the next post.
