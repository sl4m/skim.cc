---
layout: post
title: a scenario where tests help facilitate compatibility and communication 
date: 2010-12-01 23:59:00 -05:00
categories:
  -- apprenticeship
---

*tl;dr*

### Short History Lesson

Let's start off with some backstory: there was a time when only one Ruby implementation existed in the world - Matz's own Ruby Interpreter (MRI) written purely in C.  Some time later, JRuby arrived onto the scene, while it was still in its infancy, an announcement was made by [Evan Phoenix](http://twitter.com/evanphx) for a project called [Rubinius](http://rubini.us/).  Rubinius was not just an ordinary Ruby implementation; it was an implementation with a goal to be written in Ruby as much as possible, inspired and modeled off of Smalltalk\-80.  Soon thereafter, [Brian Ford](http://github.com/brixen) joined forces with Phoenix to continue Rubinius development under Engine Yard and to work on a specialized framework called [MSpec](http://github.com/rubyspec/mspec).  This simplistic framework allowed the Rubinius team to create tests of "correct behaviors" found in MRI and to mimic those results in Rubinius.  It was a basic idea designed to measure the progress of the project, and it reaped rewards far more than originally anticipated.  [RubySpec](http://rubyspec.org/) became the name of the collection of "correct behavior" tests and the executable specification for all implementations in the Ruby ecosystem.  By having all implementations follow the standard definition of Ruby (which in this case were MRI and KRI aka YARV), programmers would be able to move around to different implementations with ease and confidence.

### RubySpec on Communication

As it stands, all Ruby implementations adhere to RubySpec.  We now know how RubySpec facilitates compatibility among each implementation, but how does it facilitate communication?  RubySpec tests are not only intended to be executed against implementations, but like any other open source project, it fosters contributions.  Implementers and even developers are encouraged to add tests to RubySpec to enhance and increase the value and quality of the test suite.  By adding tests, it creates [an opportunity](http://groups.google.com/group/rubyspec/) for implementers of different implementations to talk to each other.  This is what I would call a symbiotic relationship, one where all implementers have a common goal to make their implementations look and feel the same as MRI/KRI.  

### The Case of Other Languages

[1]: http://en.wikipedia.org/wiki/Comparison_of_layout_engines_(ECMAScript)

Unfortunately, this symbiotic relationship does not appear in other languages such as JavaScript and Smalltalk (at least not yet).  JavaScript implementers took the specification from ECMA ([ECMA\-262, Edition 3](http://www.ecma-international.org/publications/standards/Ecma-262-arch.htm)), complied with [most of what was in the specification][1], and added their own language feature set on top.  Over time, after revisions and rewrites of their [JavaScript engines](http://en.wikipedia.org/wiki/JavaScript_engine), it became difficult from a developer standpoint to distinguish between what was originally part of ECMAScript and what was part of the implementation.  Perhaps that was never the goal of ECMAScript, but the language slowly became fragmented, if ever so slightly, and developers found it challenging to switch between platforms (in this case, browsers). 

Smalltalk implementers also took the specification from [ParcPlace](http://en.wikipedia.org/wiki/Parc_Place_Systems) ([Smalltalk ANSI standard](http://www.smalltalk.org/versions/ANSIStandardSmalltalk.html)) and proceeded in different directions, never to look back.  If you search in Google, "Smalltalk" and "Balkanization", you will come up with some interesting [articles](http://www.threeriversinstitute.org/blog/?p=466) on why Smalltalk did not really take off.

While some will argue that both JavaScript and Smalltalk are backed by proprietary vendors and, therefore, not in their best interests, Ruby has proprietary vendors as well.  Fortunately, though, most of the implementations are open sourced and all of them use RubySpec.  Companies like Engine Yard, Microsoft, Apple, and Gemstone have created their own implementations and, while only two of them are fully implemented, developers are excited about using them and have confidence that the language they have grown to love will work the same in the new implementation.

### What Can Be Done (Or Is It Too Late)?

Thanks to JavaScript developers like [Juriy Zaytsev](http://perfectionkills.com/), there is a [set of tests](http://kangax.github.com/cft/) that implementers can use to find common ground in the JavaScript language.  There is also the [Sputnik][http://en.wikipedia.org/wiki/Sputnik_(JavaScript_conformance_test)] test suite which determines how well an implementation adheres to ECMA\-262, 3rd Edition.  Of course, it is up to the implementers to consider trying to find common ground, but having a set of tests will reveal incompatibilities across JavaScript implementations.

For Smalltalk, there has been apparently [more converging than diverging in the past decade](http://www.threeriversinstitute.org/blog/?p=466), but we may never see the light at the end of the tunnel.  Now reaching its thirties, and with all implementations being backed by proprietary vendors, finding a common ground may prove to be difficult.  As of yet, there is no standard test suite that all Smalltalk implementers use and, as a result, communication through tests does not occur.  It may be too late because of the complexity involved with each implementation.  The only thing Smalltalk implementers have going for them is whether or not Seaside runs on their implementation, similar to how Ruby implementations use Rails ("The Rails Singularity") to test their own implementations.  

### Final Thoughts

Tests are an important part of software development.  This is one particular case where tests can help a language ecosystem thrive and sustain compatibility and communication.  I propose this is one of the reasons why we love Ruby so much.  Having common ground allows developers to fiddle with different implementations without worrying about syntactical issues, but at the same time, having the confidence that their code will work much the same way as it did from one implementation to another. 

### References

* [What is RubySpec?](http://blog.brightredglow.com/2009/3/3/what-is-rubyspec)
* [Chatting with Evan Phoenix](http://www.akitaonrails.com/2008/02/11/chatting-with-evan-phoenix)
* [The Value of the RubySpecs](http://blog.emptyway.com/2008/04/27/the-value-of-the-rubyspecs/)
* [Smalltalk: Welcome to the Balkans](http://www.threeriversinstitute.org/blog/?p=466)
* [Nash Equilibrium](http://en.wikipedia.org/wiki/Nash_equilibrium)
* [Smalltalk and Balkinzation](http://www.jarober.com/blog/blogView?showComments=true&printTitle=Balkanization_and_Smalltalk&entry=3443331580)
* [JavaScript Engine](http://en.wikipedia.org/wiki/JavaScript_engine)
* [List of ECMAScript Engines](http://en.wikipedia.org/wiki/List_of_ECMAScript_engines)
