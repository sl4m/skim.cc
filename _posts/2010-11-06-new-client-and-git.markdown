---
layout: post
title: new client and git
date: 2010-11-06 14:00:00 -05:00
categories:
  -- client
  -- rails
  -- git
---

*Note:* This post should've probably been a tweet.

## New Client

I worked with Paul yesterday to integrate a pdf generator in a Rails project.  The code that generates the pdfs is written in Java and called within Rails via JRuby.  On the Java side, we implemented the template pattern to make the code as DRY as possible.  Paul gave me access to the GitHub repo and access to the staging server.  I plan to fiddle around with it over the weekend and pick up Rails again to familiarize myself with the dsl.

## Lunch 'n' Learn - Git Session

Craig presented his final session on Git, talking in detail about branching, merging, rebasing, and tagging.  It was nice to see in detail why some merges are fast forwards, recursive, and conflicted.  I've been merging lately, but will start rebasing for future commits.
