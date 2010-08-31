---
layout: post
title: node.js knockout aftermath
date: 2010-08-30 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
  -- metaprogramming
---

Today was the day to demo our Rails features to the customer.  Paul and Craig were onsite with the customer and showed them the new features.  While some features worked, the rake task feature had some problems.  I ssh'd into one of their staging servers to look into the issue.  They were running Ruby version 1.8.6 and I tested in an environment that had 1.8.7, so I installed rvm to install 1.8.7 (Note: there may be rvm issues in different Linux distros.  I highly recommend checking out the [rvm documentation index](http://rvm.beginrescueend.com/) under Operating Systems and Packages).  After installing the required gems, I ran the rake task and saw the exact same error Paul showed me earlier in the day.  I opened the task using vi and added a bunch of debug statements, only to find out during the User\#register call, it sends out an email.  However, some users in the database do not have emails, so this is where it's blowing up (net/smtp blows up).  Unfortunately, I could not replicate this error in the local environment, so I'm looking into figuring out how to register a user that does have an email.  Hopefully, Paul will shed some light on what he wants me to do.

I forgot to mention last night that I watched Paolo Perrotta's [A Metaprogramming Spell Book talk](http://rubykaigi.tdiary.net/20100829.html) from Ruby Kaigi.  I really enjoyed his talk as he went through the Ruby Object Model (including eigenclass) and explaining on some level how Rails framework was designed.  He included snippets or "spells" from his Metaprogramming Ruby (same guy) book on his [blog](http://ducktypo.blogspot.com/2010/08/metaprogramming-spell-book.html) and explained most of them in the talk.  At the end, he explained while metaprogramming should not necessarily be used freely, it's important to understand the power of what it can do.  Don't be afraid to look under the hood.
