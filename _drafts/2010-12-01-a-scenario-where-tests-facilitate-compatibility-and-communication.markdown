---
layout: post
title: a scenario where tests help facilitate compatibility and communication 
date: 2010-12-01 23:59:00 -05:00
categories:
  -- apprenticeship
---

### Short History Lesson

Let's start off with some backstory: there was a time when only one Ruby implementation existed in the world - that implementation was Matz's own Ruby Interpreter (MRI) written purely in C.  Some time later, JRuby came out onto to the world, still an infant in its own right, and shortly after, an announcement was made by Evan Phoenix for a project called [Rubinius](http://rubini.us/).  Rubinius was not just an ordinary Ruby implementation, it was an implementation with a goal to be written in Ruby as much as possible, inspired and modeled off of Smalltalk\-80.  Soon thereafter, [Brian Ford](http://github.com/brixen) joined forces with Evan to continue Rubinius development under Engine Yard and work on a specialized framework called [MSpec](http://github.com/rubyspec/mspec).  This simplistic framework allowed the Rubinius team to create tests of "correct behaviors" found in MRI and mimic those results in Rubinius.  It was a simple idea to measure the progress of the project, and it reaped rewards possibly far more than originally intended.  [RubySpec](http://rubyspec.org/) became the name of the collection of "correct behavior" tests and became the executable specification for all implementations in the Ruby ecosystem.  By having all implementations follow the standard definition of Ruby (which in this case is MRI and KRI aka YARV), programmers will be able to move around to different implementations with "ease and confidence."

### RubySpec on Communication

As it stands, all Ruby implementations adhere to RubySpec.  We now know how RubySpec facilitates compatibility among each implementation, but how does it facilitate communication?  RubySpec tests are not only intended to be executed against implementations, but RubySpec, like any other open source project, encourages contributions.  Implementers and even programmers are encouraged to add tests to RubySpec to enhance and increase the value and quality of the test suite.  By adding tests, it sets up [an opportunity](http://groups.google.com/group/rubyspec/) for implementers of one implementation to talk to other implementers.  This is what I would call a symbiotic relationship where all implementers have a common goal \- to make their implementations look and feel the same as MRI/KRI.  

### Other Languages

Unfortunately, this symbiotic relationship does not appear in other languages like JavaScript and Smalltalk (at least not yet).  

### What Can Be Done (Or Is It Too Late?)

I think JavaScript implementers are starting to 

For Smalltalk, it may be too late.  Now reaching in its thirties, and all implementations backed by proprietary vendors, finding a common ground may prove difficult especially when there is competition.  

### References

* [What is RubySpec?](http://blog.brightredglow.com/2009/3/3/what-is-rubyspec)
* [Chatting with Evan Phoenix](http://www.akitaonrails.com/2008/02/11/chatting-with-evan-phoenix)
* [The Value of the RubySpecs](http://blog.emptyway.com/2008/04/27/the-value-of-the-rubyspecs/)
* [Smalltalk: Welcome to the Balkans](http://www.threeriversinstitute.org/blog/?p=466)
* [Smalltalk and Balkinzation](http://www.jarober.com/blog/blogView?showComments=true&printTitle=Balkanization_and_Smalltalk&entry=3443331580)


Here's a nice scenario where tests help language implementers write implementations  [RubySpec](http://rubyspec.org/) is an executable specification for Ruby.  In other words, it's a language specification for the Ruby programming language, and can be run to make sure the specification is met.  Currently, all major Ruby implementations use RubySpec.  One of the reasons they use it is to make sure the implementation is compatible.  Having a standard

If you have used Ruby before, chances are you have played around with more than one implementation (thanks to [rvm](http://rvm.beginrescueend.com/)).  Have you noticed any major differences?  Probably not\*.

I've noticed a pattern in certain languages where the implementations of each language were implemented differently from one to the other.  From the user's perspective, this can be somewhat confusing and frustrating especially when the implementation's primary purpose is to support a new environment.  Take for example, this piece for 

It's not so apparent in JavaScript, but more so with Smalltalk.

Tests not only reveal design


If you take a look at [kangax's](http://twitter.com/kangax) tweets, he always finds differences between different browsers' JavaScript engine.

[Acid3](http://acid3.acidtests.org/) test is a start for creating a 

[RubySpecs](http://rubyspec.org/) is an executable specification for Ruby.  It's designed so that all major Ruby implementations share a common ground.   

\* With exception to C extension libraries
