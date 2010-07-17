---
layout: post
title: day 1 of ruby midwest
date: 2010-07-17 12:00:00 -05:00
categories:
  -- software craftsmanship
  -- conference
---

Here are my favorite talks of the day.  Starting with Chris Wanstrath ([@defunkt](http://twitter/com/defunkt))'s keynote, he listed ways to improve OSS projects and ways to improve the overall experience to the user.  He gave project examples of what worked and what didn't work.  Here is a partial list of ways to improve OSS experience:

    * be a lazy maintainer - write a road map of the features you want in the project
    * convert README to man pages
    * create a maintainer/contribution guide
    * use semantic versioning
    * (too few and too many releases) == bad
    * it's much harder to remove a feature than to accept it
    * non-maintained projects should SAY SO!
    * documentation is a good thing
    * make installation process super simple
    * make the API human-friendly
    * always have a license file for projects
    * google your project name before you make it official
    * small projects should not have a domain especially if you do not plan to renew the domain fee

Projects that work

* Rails
* jQuery
* Homebrew
* DJango
* Unicorn

*JRuby by Charles Nutter*

Lately I've been using JRuby for my Tic Tac Toe project, so this talk was useful.  Here are my notes from the talk:

<ul>
<li>supports native threads with concurrency</li>
<li>trinidad is a thread-safe, one-process (<a href="http://calavera.github.com/trinidad/">gem</a>)</li>
<li>run in thread safe mode</li>
<li>scaling is awesome with one process!</li>
<li>-J-Xmx128M</li>
<li>Use any Javal library like it’s a Ruby library</li>
<li>No-compile single-file deployments</li>
<li>Cross-platform GUI libraries</li>
<li>tooling and maturity
<ul><li>debugging tools</li>
<li>profiling, memory tools</li>
<li>commercial jvm environments</li></ul></li>
<li>tools
<ul><li>jruby -J-Xrunhprof:format=b,depth=15 -J-Djruby.reify.classes=true memory_example.rb</li>
<li>jhat -J-Xmx200M java.hprof</li>
<li>go to http://localhost:7000/</li>
<li>jvisualvm</li></ul></li>
<li>new frontiers
<ul><li>google app engine</li>
<li>java, python, jruby</li>
<li>android</li>
<li>java mostly (or jruby)</li>
<li>anywhere with a java server</li>
<li>deploy like any other application</li></ul></li>
<li>ruboto
<ul><li>gem install ruboto</li>
<li>ruboto generate app</li>
<li>ruboto release</li></ul></li>
<li>three full-time devs at engine yard</li>
</ul>

There are two [Ruby Summer of Code](http://rubysoc.org/) projects that are contributing to JRuby.  One of them is support for C extensions in JRuby.  As of now, a good number of tests passing for [Thin](http://code.macournoyer.com/thin/).  The other project is for the Ruboto project which allows you to write Ruby code to create Android apps.  Soon enough, you'll be able to install the ruboto gem, generate the app, write Ruby code, and release it to the Android Market.

Blog posts on jmap/jhat, VisualVM here: [[1](http://blog.headius.com/2010/07/browsing-memory-jruby-way.html)][[2](http://blog.headius.com/2010/07/finding-leaks-in-ruby-apps-with-eclipse.html)]

*Unobtrusive CSS by John Hwang*

I'm a CSS noob, so this was a nice opener to CSS and understanding the underlying problems people experience with plain CSS.  There are CSS frameworks, semantic/meta frameworks that try to resolve the problems in CSS:

* lack of abstractions
* repetitive selectors (not DRY)
* difficult to control layouts
* efficiency/organizational issues
* code re-use is non-existent
* code organization is non-existent
* file size just keeps getting better
* difficult to maintain or change

CSS frameworks...

* promote grid layouts
* best practices
* sensible defaults
* reset CSS
* typography

but problems are present:

* nothing more than a collection of CSS snippets
* tight coupling of presentation and content
* almost as bad as using table layout

In John's ([@tavon](http://twitter.com/tavon)) point of view, CSS meta frameworks are the way to go, especially [Sass](http://sass-lang.com/).

Sass...

* has nested rules
* has variables
* has mixins
* compiles and outputs CSS
* fully CSS3 compliant (SCSS syntax)
* Turin complete language
* Firebug integration
* selector inheritance

With meta frameworks like Sass, you can build unobtrusive stylesheets which allows:

* faster implementation
* faster change design
* flexibility for theming and alternate stylesheets
* easier redesigns

*Lightning Talks*

During the [OMGWTF BBQ](http://omgwtfbbq.heroku.com/), there were 7 or 8 lightning talks.

*Mirah by Charles Nutter*

[Mirah](http://www.mirah.org/) (formerly Duby) is a new programming language that allows you write code that looks syntactically like Ruby, but compiles down to fast JVM bytecode.  Charlie ([@headius](http://twitter.com/headius))gave a couple of performance examples.  Mirah was pretty fast compared to Ruby MRI.  I look forward to seeing this project grow and plan to try it out in the near future.

*Fog by Wesley Beary*

Wesley ([@geemus](http://twitter.com/geemus)) presented his cloud computing gem that helps interact with cloud services easily.  It currently supports the following cloud-based services:

* Amazon Elastic Computer Cloud (EC2)
* Amazon Simple Storage Service (S3)
* Amazon SimpleDB
* Rackspace Files
* Rackspace Server
* Slicehost
* Terremark vCloud Express

I will post about day 2 tomorrow.
