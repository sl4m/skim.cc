---
layout: post
title: fitnesse and acceptance tests
date: 2010-10-01 12:00:00 -05:00
categories:
  -- software craftsmanship
  -- yak shaving
  -- java
  -- stories
  -- fitnesse
  -- slim
  -- acceptance tests
---

![FitNesse Architecture](/images/fitnesse_architecture.jpg)

One of my stories calls for creating a FitNesse/Slim tests for my Limelight styles converter.  I went to the [FitNesse](http://fitnesse.org/) website to read about [FIT](http://fitnesse.org/FitNesse.UserGuide.FitFramework) (Framework for Integrated Testing), what FitNesse provides to the user, and how to get it [set up](http://fitnesse.org/FitNesse.UserGuide.DownloadingAndInstallingFitNesse) on my machine.  The installation process is super simple.  Place the jar file in an empty directory and run:

{% highlight text %}
[~/local/fitnesse] java -jar fitnesse.jar -p 34863
FitNesse (v20100303) Started...
	port:              34863
	root page:         fitnesse.wiki.FileSystemPage at ./FitNesseRoot
	logger:            none
	authenticator:     fitnesse.authentication.PromiscuousAuthenticator
	html page factory: fitnesse.html.HtmlPageFactory
	page version expiration set to 14 days.
{% endhighlight %}

It creates a FitNesseRoot folder and launches the webserver.  Navigating to [http://localhost:34863](http://localhost:34863) opens up the FitNesse homepage.

In the diagram above, you'll notice two different types of test systems: Slim and Fit.  [Slim](http://fitnesse.org/FitNesse.UserGuide.SliM) (Simple List Invocation Method) is what I'll be using with FitNesse.  Fit is the older test system (and not really used anymore?).

The basic idea is to create a fixture that connects the test tables with actual code that does the real work.  In my case, I'll need to create a fixture that reads from the test table and call from my LLStyles class to do the real work, that is, parse the Limelight styles.rb and display Java code.  Since the LLStyles class currently displays the code to stdout, I'll need to add support of returning the Java code from the method.  More on this later.

## Agile Software Development, Principles, Patterns, and Practices

I did a bit of reading a couple of nights ago and went through the list of XP practices:

* Customer Team Member
* User Stories
* Short Cycles
* Acceptance Tests
* Pair Programming
* TDD
* Collective Ownership
* Continuous Integration
* Sustainable Pace
* Open Workspace
* The Planning Game
* Simple Design
* Refactoring
* Metaphor

I like how I see all of these practices in place at 8th Light.  One interesting tidbit I read regarding "open workspace" was how a ["war room" like environment doubles productivity](http://www.sciencedaily.com/releases/2000/12/001206144705.htm).  You'd think it would be distracting to hear other people's conversation, but it's actually nice to hear what's going on with the other projects and people can chime in if someone needs help or a [rubber ducky](http://www.c2.com/cgi/wiki?RubberDucking).
