---
layout: post
title: http server in java - concurrency
date: 2010-10-07 21:30:00 -05:00
categories:
  -- software craftsmanship
  -- yak shaving
  -- java
  -- http server
  -- apprenticeship challenge
  -- concurrency
---

An HTTP server handles more than one request at a time.  Since it's very much possible that more than one request can come in at the same time, the "listener" needs to run concurrently and create more tasks to process every client's request.  This is the heart of the topic for today's blog post.

### References used

* Chapter 10: Concurrency in Effective Java 2nd Edition (thanks Colin!)
* Craftsman Articles \#6\-10 (thanks Justin!)
* LinkedList, ExecutorService in Java Doc (thanks Sun?)
* Decorator Pattern in Head First : Design Patterns

## The synchronized keyword

> "Synchronization is required for reliable communication between threads as well as for mutual exclusion."

In Java, *synchronized* is used to "ensure that only a single thread can execute a method or block at one time.  This allows multiple threads to observe objects in a consistent state as well as ensure each thread knows about the modifications other threads have made when entering in the synchronized method.

> "...synchronization has no effect unless both read and write operations are synchronized."

One way for threads to communicate with each other is the use of a boolean (or any data type).  In the main thread, the boolean is created and initially set to false, and the child thread is started and will continue to run until it sees the boolean set to true.  Both reading and writing to this boolean needs to be synchronized, otherwise, it's possible for the child thread to never see the new value for the boolean set by the main thread.  

> "...when multiple threads share mutable data, each thread that reads or writes the data must perform synchronization."

The author explains the best way to avoid inconsistent state is to "confine mutable data to a single thread."  Unfortunately, the way things are looking, I will need mutable data to be shared across threads, so I will most likely be using a form of synchronization.

## Prefer executors and tasks to threads

Starting with Java 1.5, *java.util.concurrent* was added to the Java platform and offers an Executor Framework, a flexible interface-based task execution facility.  This has many advantages over creating and managing threads on your own.  For example, it can:

* wait for a particular task to complete
* wait for a collection of tasks to complete
* wait for the executor service's graceful termination to complete
* retrieve the results of each task

The Effective Java author states that you should not write your own work queues nor should you work directly with threads.  It sounds to me, like working with threads is a thing of the past.  Thread served as both the unit of work and mechanism for executing it..  Now they are separate with the Executor Framework.  *task* is the unit of work and *executor service* is the mechanism for executing tasks (Item 68, p.272).

Fortunately, Colin will bring a book called Java Concurrency in Practice which goes into more detail about the Executor Framework.  I look forward to using this as a way to create and manage tasks (e.g., responding to client requests, reading static files).

## Decorator Pattern

The [Decorator pattern](http://en.wikipedia.org/wiki/Decorator_pattern) is used in implementations of the List interface.  *Collections.synchronizedList* method wraps a list in a decorator to prevent accidental, unsynchronized access to the list when making structural modifications (e.g., adding/removing elements).

I read the Decorator Pattern in Head First and didn't know the pattern was used for concrete components of InputStream class (e.g., FileInputStream, StringBufferInputStream, BufferedInputStream), but it makes sense now.  I recommend reading the example that they show in the book if you want to know more about the pattern.

## Observer Pattern

*Note:* While this pattern does not tie into the concurrency topic, it was mentioned in the Concurrency chapter of Effective Java, so I thought I'd mention it.

The [Observer pattern](http://en.wikipedia.org/wiki/Observer_pattern) is a loose coupling relationship between a publisher and one or more subscribers.  The publisher (or subject) maintains a list of the subscribers (or observers) and notifies them when there are changes within the publisher.  The subscriber has the ability to subscribe to a publisher to receive notifications and unsubscribe if it no longer wants notifications.  While Java has a built-in Observable class, it's a class and therefore an existing class that extends another class cannot use Observable.  To make things worse, it's impossible to utilize the built-in Observer because there is no Observable interface.  In the end, if the built-ins do not work for you, you can easily roll your own implementation.
