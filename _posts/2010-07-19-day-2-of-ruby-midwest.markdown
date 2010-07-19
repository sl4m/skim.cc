---
layout: post
title: day 2 of ruby midwest
date: 2010-07-19 12:00:00 -05:00
categories:
  -- software craftsmanship
  -- conference
---

Here are my favorite talks for Day 2 of Ruby Midwest.  [Yehuda Katz's](http://twitter.com/wycats) keynote was similar to Chris Wanstrath's, touching on the importance of the Ruby community.  He called the Ruby community, "a blessing and a curse" because it :

* enjoys experimenting with new projects
* does not put up with crap 
* expects basic commands to run without reading the manual
* expects a high level of UX
* expects support for all platforms, unique environments (e.g., Windows, JRuby, Passenger, rvm, Unicorn, gemcutter)
* expects the project to work with other gems
* expects maturity of a project
* expects proper maintenance and frequent releases

He listed four phases of his life as a Ruby developer:

* Phase One : Noob
* Phase Two : Aspiring Plugin Author
* Phase Three : OSS Contributor
* Phase Four : Full-time OSS at Engine Yard

Like everyone else, he started off as a noob, using Windows as his primary OS, building small Rails apps for a non-proft.  He called it a time of confusion, because he did not know things like methods, etc.  But of course, that didn't stop him from becoming an aspiring plugin author, building plugins such as autodb and yhtml.  As an OSS contributor, he contributed to projects like DataMapper and Merb.  Merb had a following and Rubyists were switching to Merb from Rails because they love trying out new projects, even though the project was not stable and contained bugs.  While disrupting the Ruby ecosystem (as Merb did) can be a good thing to bring constructive competition, it can also breed arrogance and can leave stable, working projects unnoticed (Rails).  In the case of Merb though, features that were great in Merb, integrated into Rails after the Rails-Merb merge.

Yehuda strongly encourages OSS contributors to

* give high-level UX to the users
* make sure basic commands work and does not require a manual
* make sure all platforms, special environmental factors are supported
* be excited if the first project takes your ideas (e.g., Rails vs Merb)
* continue contributing to the project for the long haul if you're the primary maintainer
* continue contributing to the project even after the "hype" dies
* make sure the next person is in it for the long haul if they decide to jump ship
* announce the project is no longer maintained and in need of a new maintainer

Yehuda strongly encourages the Ruby community to

* reward long-term maintainers
* encourage up-and-coming projects to mature
* push mature projects to improve UX
* become a maintainer
* expect reading the manual for complex commands

[Wesley Beary](http://twitter.com/geemus) also had a similar talk on UX.  Here are some bullet points:

* do not worry about competition (it's a good thing)
* "tutorialize" - as a maintainer of the project, help out as much as possible (e.g., IRC)
* encourage contributors

Aman Gupta talked about memprofiler.  I listened to his talk with Joe Damato at LA Ruby earlier this year, but most of it was over my head.  Listening to it again months later, I mostly understand the power of memprofiler and how it can help you find bottlenecks in your code.  Here are my notes:

<ul>
<li>Ruby's GC (garbage collector) does not scale as object count increases</li>
<li>More objects == longer GC time, fewer objects == better performance</li>
<li>When GC is running, nothing else runs which pads response time.</li>
<li>useful tools
<ol><li>ObjectSpace.each_object</li>
<li>ObjectSpace.count_objects (in Ruby 1.9)</li>
<li>gdb.rb: gdb hooks for REE (<a href="http://github.com/tmm1/gdb.rb">http://github.com/tmm1/gdb.rb</a>)
<ul><li>linux only</li></ul></li>
<li>bleak_house
<ul><li><a href="http://github.com/fauna/bleak_house">http://github.com/fauna/bleak_house</a></li>
<li>installs a custom patched version of ruby</li>
<li>tells you what is leaking, and also where</li></ul></li>
<li>heap dumping patches
<ul><li>simple patch to ruby VM</li>
<li><a href="http://gist.github.com/73674">http://gist.github.com/73674</a></li>
<li>simple text based output format</li></ul></li>
<li>memprof
<ul><li>easy to use</li>
<li>no patching the VM</li>
<li>just require the gem</li>
<li>includes file/line, object contents, info about references between objects</li>
<li>simple analysis</li>
<li>allow processing via various languages and databases using simple JSON data format</li>
<li><a href="http://github.com/ice799/memprof">http://github.com/ice799/memprof</a></li>
<li>gem install memprof</li>
<li>use ruby 1.8.x</li>
<li>under active development</li>
<li>how it works</li>
<li>rewrites your ruby binary in memory</li>
<li>injects short trampolines for all calls to internal VM functionals to do tracking</li>
<li>more info - <a href="http://timetobleed.com">http://timetobleed.com</a></li>
<li><a href="http://bit.ly/memprof-abi">http://bit.ly/memprof-abi</a></li>
<li>memprof features</li>
<li>memprof.track
<ul><li>Memprof::Middleware</li></ul></li>
<li>memprof.dump
<ul><li>detailed info about block in JSON</li></ul></li>
<li>memprof.dump_all
<ul><li>dumps out every single live object as json</li>
<li>one per line to specifed file</li></ul></li>
<li><a href="http://memprof.com">http://memprof.com</a>
<ul><li>web-based heap visualizer and leak analyzer</li>
<li>built using rails 3 app</li></ul></li></ul></li></ol></li>
</ul>

Unfortunately, I didn't stick around for Cory Flanigan's Zero to Hero talk which I heard was really good.  Overall, the conference was great.  I'm glad I attended and look forward to next year's.  Hopefully by then, I'll give a talk on something.  Kansas City is a great city.  I look forward to coming back again soon for a nice weekend vacation.  If you ever decide to visit to KC, be sure to check out [Fresher than Fresh Snow Cones](http://twitter.com/FTFsnowcones).
