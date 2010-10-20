---
layout: post
title: five design patterns
date: 2010-10-20 11:00:00 -05:00
categories:
  -- design patterns
  -- tic tac toe
  -- solid
  -- uml
---

> "When we consider using a pattern, we must decide whether the pattern solves the problem, whether it fits the context, and whether the benefits outweigh the costs." - [Uncle Bob Martin](http://today.java.net/pub/a/today/2004/06/8/patterns.html)

I will go over the five design patterns I learned:

* Abstract Server
* Abstract Factory
* Observer
* Strategy
* Template Method

### Abstract Server

This pattern is considered one of the simplest patterns of all OO design patterns.  It is used to break dependency of client and server and prevents DIP violation, and therefore prevents OCP violation.  Although, it has the word "server" in it, it has nothing to do with a server.  In Uncle Bob's [article](http://today.java.net/pub/a/today/2004/06/8/patterns.html), he uses a button/light example to show how this pattern can be used.  DIP says:

> "Depend on abstractions, not on concretions"

The button depends on light.  The solution is to introduce an interface called Switchable in between the two concrete classes.  The concrete class and derivative class now point to the new interface.  The name of the interface is pretty interesting.  It's not named similarly to the derivative, but with the client.  This is because the interface belongs to the client and will be packaged together.  When thinking about static languages, it is important to package classes/interfaces together to avoid the need to re\-compile.  As the PPP (Principles, Patterns, and Practices) book says, "the logical binding between the client and the interface is stronger than the logical binding between the interface and its derivatives."

### Abstract Factory

Textbook definition: Provide an interface for creating families of related or dependent objects without specifying their concrete classes.

This pattern basically takes away concrete class references from the client and moves them to a concrete factory class.  An abstract factory class is then used to prevent DIP violation and sits in between the client and the concrete factory class.  In the concrete factory class, you'll have a method like "make" that will take a string argument of the name of the concrete class you want to instantiate.  I asked Micah about the if/else statement in the factory class.  He said it's ok to use since it's used to instantiate classes.

Abstract Factory uses Strategy \- abstract factory class with concrete factory classes.

### Observer

Textbook definition: Define one\-to\-many dependency between objects so that when one object changes, all its dependents are notified and updated automatically.

This is a subset of the [pub/sub](http://en.wikipedia.org/wiki/Publish/subscribe) pattern.  A publisher allows subscribers to subscribe/unsubscribe notifications.  Micah gave an example about a Clock client.  If another class wants to get the time for every millisecond, or nanosecond, etc., it's better to tell the class that the time has updated instead of the class asking if the time updated.  This is especially true when there are more than one class asking.  Will each class have a while loop and ask forever?  An observable class will notify all of its subscribers (or observers) and each observer will then get information from the observable or execute other commands specific to its needs.

### Strategy

Textbook definition: Define a family of algorithms, encapsulate each one, and make them interchangeable.  Strategy lets the algorithm vary independently from clients that use it.

The Strategy pattern is about taking advantage of polymorphism.  It allows you to easily swap different algorithms.  Uncle Bob illustrated a Logger class that allows for different types of formats and different types of recording the logs.  Strategy says create an interface called Recorder and have all derivatives define the "algorithm".  So the RamRecorder derivative class will have an algorithm to write to memory, FileRecorder will have an algorithm to write to file, and so on.

### Template Method

Textbook definition: Define the skeleton of an algorithm in an operation, deferring some steps to subclasses.  Template Method lets subclasses redefine certain steps of an algorithm without changing the algorithm's structure.

Template Method is similar to Strategy except it has some implementation to the algorithm and leaves it up to the derivatives to finish the implementation.  There might be situations where two derivatives will perform the same kinds of the steps in the beginning or the end, but in the middle is where it's actually different.  By using Template Method, you can move the duplicate code up to the base class and only have different code in the derivatives (keeps it DRY).

## Implementing design changes to Tic Tac Toe

I went ahead and made changes to my Tic Tac Toe implementation in Java.  I introduced Abstract Server, Abstract Factory.  I created interfaces and abstract class for Board, UI, and Player.  I then ended up with several factories to create the Board, UI, and Player.  I thought I could introduce Template Method to each player's makeMove method, but I noticed Game actually places a move on the board after getting the move from Player.  This is because it checks to make sure the move is valid.

This was a great exercise.  I'm glad to have learned about these five design patterns and look forward to learning all of them (from the Design Patterns book).

## References

* Design Patterns by GOF
* Agile Software Development PPP
* Uncle Bob [articles](http://www.java.net/author/robert-c-martin)
