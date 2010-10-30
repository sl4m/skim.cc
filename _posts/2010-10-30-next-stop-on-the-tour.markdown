---
layout: post
title: next stop on the tour
date: 2010-10-30 15:00:00 -05:00
categories:
  -- client
  -- ruby
---

My next stop on the apprenticeship tour, I'll be working with Jim and the two Erics.  There are multiple projects for this particular client and they're using Rails among other technologies.  I spent most of yesterday getting the development environment set up, making sure all tests ran successfully.  I've not worked on a project with so many unit tests, so it will be pretty interesting.  While it took me about half a day to get set up, it should only take a couple of hours.  I ended up creating several wiki pages on FitNesse for instructions on how to set up subversion and the development environment for Snow Leopard using rvm and homebrew.  The next person taking on these projects should be able to easily get the environment up and going in less time than me.

## 8LU - Git Session by Craig

Craig continued his git series by talking in depth about a lot of git commands.  Most I knew about, but there were some that I was not aware of, so it was nice to learn about them.  One particular thing I learned from Craig and try to follow on projects is to create a local branch when making changes, then rebase master on top when ready to push changes to GitHub.  Here are the steps:

* pull latest from GitHub repo to local master
* checkout new branch (e.g., git checkout \-b new\_branch)
* work on stuff
* commit stuff on new\_branch
* checkout master and pull changes
* checkout new\_branch and rebase master on top of new\_branch
* push changes
* delete new\_branch

I look forward to his next git session next week.  It should hopefully cover some good topics on branching and merging.

## 8th Light Hack Night

This is the first 8th Light hack night I participated.  We're going to make some improvments to the 8th Light website and one of the things I'm doing is to add the Twitter profile links to each craftsman's page.  I already have what I need and will be getting it done today.
