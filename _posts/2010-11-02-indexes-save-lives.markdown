---
layout: post
title: indexes save lives
date: 2010-11-02 20:00:00 -05:00
categories:
  -- client
  -- ruby
---

Eric Meyer and I were able to identify the problem of the long running process from yesterday.  By creating a composite index, in one of the tables, it looks like we solved the problem!  We checked the logs and saw each SQL query took anywhere from 1-5 seconds before the index and 0.0002-0.0007 seconds after the index.  A dramatic improvement and significant time reduction.  Eric and Jim will be working on it further tomorrow to see if it truly fixed the problem.

The next task Eric and I started working on was seeing if Selenium tests were able to run on a Solaris environment.  I quickly checked the Selenium website and saw it was supported.  Eric took the lead and tried to make it work, but we didn't have time to finish the task.  He will continue working on it tomorrow.

Tomorrow, I plan to work with Eric Smith.

## Chicago Ruby Meetup

Justin Love presented his talk on [AMP](http://amp.carboni.ca/), a cross\-repo version source control in Ruby.  AMP is basically a one\-stop shop Ruby front end solution to two major distributed VCS: Mercurial and git.  At least, that's the idea for the upcoming project.  The original John Locke version only supports Mercurial because the developers ran into some roadblocks with git.  Since Mercurial is GPL licensed, the developers ported Mercurial to AMP and also licensed it as GPL.  The next version of AMP called AMP Redux (pronounced 'redo') will separate interface and implementation and support both Mercurial and git.  They've learned a lot from the process of creating the John Locke version and currently creating AMP Redux.

#### Why use AMP (or why another VCS)?

Justin Love listed the major VCS out there (e.g., git written in C, Mercurial written Python) and explained how there are no VCS solutions written in Ruby.  Why not?  There seems to be a general concensus that Ruby is not viable for large\-scale applications, just web frameworks.  AMP wants to prove that Ruby *is* viable as written in AMP's [manifesto](http://bitbucket.org/carbonica/amp/src/ef141288db29/MANIFESTO).  Here's what else it says:

* Is free of religious devotion to one VCS
* Lets us customize how we interact with it
* Lets us create extensions to add features for all supported VCS
* Lets us customize default commands as well as new
* Discover the limits of Ruby
* Be an example of proper documentation

#### What can AMP do?

The John Locke version currently supports Mercurial and can access Mercurial repos like the hg command.  git, bazaar, svn, and cvs are hopeful supported VCS in AMP Redux.  Justin made an analogous comparison of AMP to ActiveRecord in Rails.  AMP wants to be like ActiveRecord.

#### How can I use AMP?

* gem install amp
* amp \-\-help

#### How can you help out?

* needs documentation
* website is in place, but doc out of date
* read TODO list

Justin will have this talk at the upcoming RubyConf in New Orleans.
