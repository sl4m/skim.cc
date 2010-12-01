---
layout: post
title: a scenario where tests help facilitate compatibility and communication 
date: 2010-12-01 23:59:00 -05:00
categories:
  -- apprenticeship
---

*tl;dr*

### Short History Lesson

Let's start off with some backstory: there was a time when only one Ruby implementation existed in the world - that implementation was Matz's own Ruby Interpreter (MRI) written purely in C.  Some time later, JRuby came out onto to the world, still an infant in its own right, and shortly after, an announcement was made by Evan Phoenix for a project called [Rubinius](http://rubini.us/).  Rubinius was not just an ordinary Ruby implementation, it was an implementation with a goal to be written in Ruby as much as possible, inspired and modeled off of Smalltalk\-80.  Soon thereafter, [Brian Ford](http://github.com/brixen) joined forces with Evan to continue Rubinius development under Engine Yard and work on a specialized framework called [MSpec](http://github.com/rubyspec/mspec).  This simplistic framework allowed the Rubinius team to create tests of "correct behaviors" found in MRI and mimic those results in Rubinius.  It was a simple idea to measure the progress of the project, and it reaped rewards possibly far more than originally intended.  [RubySpec](http://rubyspec.org/) became the name of the collection of "correct behavior" tests and became the executable specification for all implementations in the Ruby ecosystem.  By having all implementations follow the standard definition of Ruby (which in this case is MRI and KRI aka YARV), programmers will be able to move around to different implementations with "ease and confidence."

### RubySpec on Communication

As it stands, all Ruby implementations adhere to RubySpec.  We now know how RubySpec facilitates compatibility among each implementation, but how does it facilitate communication?  RubySpec tests are not only intended to be executed against implementations, but like any other open source project, encourages contributions.  Implementers and even developers are encouraged to add tests to RubySpec to enhance and increase the value and quality of the test suite.  By adding tests, it sets up [an opportunity](http://groups.google.com/group/rubyspec/) for implementers of one implementation to talk to other implementers.  This is what I would call a symbiotic relationship where all implementers have a common goal \- to make their implementations look and feel the same as MRI/KRI.  

### The Case of Other Languages

Unfortunately, this symbiotic relationship does not appear in other languages like JavaScript and Smalltalk (at least not yet).  JavaScript implementers took the specification from ECMA ([ECMA\-262, Edition 3](http://www.ecma-international.org/publications/standards/Ecma-262-arch.htm)), complied with [most of what was in the specification](http://en.wikipedia.org/wiki/Comparison_of_layout_engines_(ECMAScript)) and added their own language feature set on top.  Over time, after revisions of their [JavaScript engines](http://en.wikipedia.org/wiki/JavaScript_engine) and even new ones, it became difficult to understand what was originally part of ECMAScript and what was their own.  Perhaps, maybe that was never the goal of ECMAScript, but the language slowly became fragmented (even if ever so slightly) and developers found it difficult to switch between platforms (in this case, browsers). 

Smalltalk implementers also took the specification from [ParcPlace](http://en.wikipedia.org/wiki/Parc_Place_Systems) ([Smalltalk ANSI standard](http://www.smalltalk.org/versions/ANSIStandardSmalltalk.html)) and went off in different directions, never to look back.  If you search in Google, "Smalltalk" and "Balkanization", you'll come up with some interesting [articles](http://www.threeriversinstitute.org/blog/?p=466) on why Smalltalk didn't really take off.

While some will argue both JavaScript and Smalltalk are all backed by proprietary vendors and therefore not in their best interest, Ruby has proprietary vendors too.  Fortunately though, most of the implementations are open sourced and all of them use RubySpec.  Companies like Engine Yard, Microsoft, Apple, and Gemstone all have created their own implementations and while only two of them are fully implemented, developers are excited about using them and have confidence that the language they have grown to love will work the same in the new implementation.

### What Can Be Done (Or Is It Too Late?)

Thanks to JavaScript developers like [Juriy Zaytsev](http://perfectionkills.com/), there's a [set of tests](http://kangax.github.com/cft/) that implementers can use to find common ground in the JavaScript language.  There's also [Acid3](http://acid3.acidtests.org/) test that now support a small of set of JavaScript conformity.  Of course, it'll be up to the implementers to even consider trying to find common ground, but having a set of tests will reveal incompatibilities across JavaScript implementations.

For Smalltalk, there's apparently [more converging than diverging in the past decade](http://www.threeriversinstitute.org/blog/?p=466), but we may never see the light at the end of the tunnel.  Now reaching in its thirties, and all implementations backed by proprietary vendors, finding a common ground may prove to be difficult.  At this time of writing, there is no standard test suite that all Smalltalk implementers use and therefore communication through tests do not occur.  It may be too late because of how difficult each implementation is.  The only thing Smalltalk implementers have going is whether or not Seaside runs on their implementation, similar to how Ruby implementations use Rails ("The Rails Singularity") to test their own implementations.  

### Final Thoughts

Tests are an important part of software development.  This is one particular case where tests can help a language ecosystem thrive and sustain compatibility and communication.  I'd argue this is one of the reasons why we love Ruby so much.  Having common ground allows developers to mess around with different implementations and not have to worry about syntactical issues, but have confidence their code will work much the same way as it did from one implementation to another. 

### References

* [What is RubySpec?](http://blog.brightredglow.com/2009/3/3/what-is-rubyspec)
* [Chatting with Evan Phoenix](http://www.akitaonrails.com/2008/02/11/chatting-with-evan-phoenix)
* [The Value of the RubySpecs](http://blog.emptyway.com/2008/04/27/the-value-of-the-rubyspecs/)
* [Smalltalk: Welcome to the Balkans](http://www.threeriversinstitute.org/blog/?p=466)
* [Nash Equilibrium](http://en.wikipedia.org/wiki/Nash_equilibrium)
* [Smalltalk and Balkinzation](http://www.jarober.com/blog/blogView?showComments=true&printTitle=Balkanization_and_Smalltalk&entry=3443331580)
* [JavaScript Engine](http://en.wikipedia.org/wiki/JavaScript_engine)
* [Comparison of layout engines (ECMAScript)](http://en.wikipedia.org/wiki/Comparison_of_layout_engines_(ECMAScript))
* [List of ECMAScript Engines](http://en.wikipedia.org/wiki/List_of_ECMAScript_engines)
