---
layout: post
title: using state machine for parsing
date: 2010-09-26 23:00:00 -05:00
categories:
  -- software craftsmanship
  -- yak shaving
  -- java
  -- statemachine
---

[Finite-state automaton](http://en.wikipedia.org/wiki/Finite-state_machine") is

> "a mathematical abstraction sometimes used to design digital logic or computer programs.  It is a behavior model composed of a finite number of states, transitions between those states, and actions, similar to a flow graph in which one can inspect the way logic runs when certain conditions are met."

I'm working on the story that asks to create a jar file that will read Ruby code (Limelight styles.rb) and convert it into Java code.  My initial approach was to use regular expressions to parse the Ruby file in several different stages.  When I approached the problem to Micah this past Friday, he came up with a better solution, using a state machine to create a parser.

He gave me a nice lecture, briefly describing the [Turing machine](http://en.wikipedia.org/wiki/Turing_machine) and how state machines are said to be "[Turing complete](http://en.wikipedia.org/wiki/Turing_completeness)", then drew a [UML state machine](http://en.wikipedia.org/wiki/UML_state_machine) of a [turnstile](http://en.wikipedia.org/wiki/Turnstile) system and a table listing all possible state, event, action combinations.  Here is [his presentation](http://blog.8thlight.com/files/statemachines_chirb0407.pdf) I found on the [8th Light blog](http://blog.8thlight.com/statemachine).

He took it one step further and did the same thing for the parser in addition to drawing the UML diagram of the Java classes involved.  The UML state machine for the parser is a little bit more involved as there are more transitions (roughly 18) but it should not be too difficult to implement since the state machine code is auto-generated.

Fortunately, Micah wrote a Ruby gem called [statemachine](http://github.com/slagyr/statemachine), which I can use to generate the state machine code.  It generates it in both Ruby and Java.  All you need to do is provide a list of transitions (e.g., old state, event, new state, action).  I looked at the tests in the GitHub repo to see how Micah generates the statemachine code in Java.  I've also taken a look at the [sample exercise](http://blog.8thlight.com/articles/2007/5/8/chirb-statemachine-talk) to get an idea of how it was done in Ruby.  In short, he calls the *to_java* method to generate Java code from Ruby.  It takes three arguments: output directory, class name, and package and returns the auto-generated code in output\_directory/package\_name.

In my next post, I will explain what was involved after auto-generating the Java code.
