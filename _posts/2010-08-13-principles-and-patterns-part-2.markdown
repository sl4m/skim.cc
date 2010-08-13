---
layout: post
title: principles and patterns - part 2 
date: 2010-08-13 16:00:00 -05:00
categories:
  -- software craftsmanship
  -- principles
  -- patterns
  -- SOLID
---

I finished reading Uncle Bob's [Principles and Patterns](http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf), except for the part on Principles of Package Architecture.  After talking about the four primary symptoms that indicate rotting designs, Uncle Bob goes through the [SOLID principles](http://butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod) which are primarily about dependency management.  I was fortunate enough to find Jim Weirich's [talk on SOLID principles](http://rubyconf2009.confreaks.com/20-nov-2009-15-05-solid-ruby-jim-weirich.html) and how it applies to dynamic languages like Ruby.  I will be using his references to describe some of the SOLID principles.

## Single Responsibility Principle

> "A class should have one, and only one, reason to change"

A class should have one responsibility.  Having two responsibilities makes it less flexible for change and potentially harder to test.  An easy to way to tell if you're violating this principle is to write down the purpose of the class.  If there is an AND or OR, the class is probably doing more than one thing.

## Open Closed Principle

> "You should be able to extend class behavior, without modifying it"

Uncle Bob states this is one of the most important principles in object oriented design.  Abstraction is the key to this principle.  If you see yourself adding if/else or switch statements, this is probably an indication that it needs to be abstracted.

In Ruby, if you wanted to use a third party library, but need different behavior, instead of modifying the library, extend it.

## Liskov Substitution Principle

> "Derived classes must be substitutable for their base classes"

This is something I observed when reading about this principle.  Since Ruby supports duck typing, it's natural to substitute derived classes for their base classes.  There are two conditions that must be met for derived classes:

* it must require no more 
* it must promise no less

Jim walked through an example of a square root method which requires a number greater or equal to zero and provides an accuracy of three decimal places.  The design by contract therefore requires a number greater or equal to zero and an accuracy of three decimal places.  All derived classes must meet this requirement, otherwise will violate the Liskov Substitution Principle.

## Interface Segregation Principle

> "Make fine grained interfaces that are client specific"

Having many interfaces is more flexible than having one big interface that handles all.  Having many will not impact other interfaces when changing code for another.

## Dependency Inversion Principle

> "Depend on abstractions, not on concretions"

If you depend on concrete classes, you create explicit references and make it difficult to use other classes that like the ones you originally depended on.  By introducing an interface, you allow other classes to be used that conform to the interface.  

In Ruby, interfaces do not exist.  Fortunately, there is a style of dynamic typing called [duck typing](http://en.wikipedia.org/wiki/Duck_typing).

> "when I see a bird that walks like a duck and swims like a duck and quacks like a duck, I call that bird a duck."

Due to the dynamic nature of the language, explicit references are hard to create in Ruby.  There are no explicit interfaces, but it has something similar to what Jim calls "protocol".  The protocols, like interfaces, have a list of methods with semantics.

## Conclusion

I really recommend watching Jim Weirich's talk.  There's a lot of really good information that was not covered here.  He ends the video with this question:

> SOLID principles were designed with static languages in mind.  Are there SOLID-like principles that are specific to dynamic languages like Ruby?

He doesn't have an answer, but welcomes discussion.  I look forward to hearing about the principles.
