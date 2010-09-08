---
layout: post
title: new stories, new iteration
date: 2010-09-07 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- tic tac toe
  -- webrick
  -- java
  -- rails
  -- prime factors kata
---

It's great to be back after a long, much needed weekend.  Today, Micah (customer) and I had our end of iteration meeting where I presented a couple of stories that I worked on last week.  The first story was persisting scores for player O and X in my Tic Tac Toe project.  It works without problems in both console and Limelight and is stored via CSV.  Micah noted that while CSV may be suitable for a project like Tic Tac Toe, in real world situations, it's best to store in a database where the possibility of file corruption is minimized.  The second story was about supporting multiple players in a WEBrick environment.  Unfortunately, I was unable to finish this, but had a spiked version of the game working in a single thread.  Now I need to add session support via cookies, then throw it all away, and write it TDD style.

Micah created new stories for this new iteration.  I'm pretty excited to be working on them.  Here's the short list:

* Build Tic Tac Toe on Rails 3
* Practice Prime Factors Kata in Ruby

I wrote a post on how to [setup Rails 3 for Windows](http://skim.la/2010/08/21/rails-3-rc-on-windows-using-rubyinstaller-192) on my other blog.  Now I have a reason to build a Rails 3 app!  The points for this story is not as high because I'm somewhat familiar with Rails from the past couple of weeks of work.  There are changes to Rails convention in version 3, but not enough to slow me down.  Maybe I should write the app on my Windows box?  There shouldn't be anything different from a Unix environment.  The only external library I use is mongo gem.  We'll see...

I never expected Micah to give me a story to practice Prime Factors Kata.  When Jim presented the kata during his Node.js/Vows.js presentation, I really enjoyed writing it.  Now I need to practice it and perform the kata in front of other 8th Lighters on Friday.  Yikes.  I haven't presented anything yet to any of the 8th Lighters (except Micah and Paul), so this will be interesting.  I hope no one shows up.  I'm kidding.

I made sure to ask Micah all questions about each story before we finished our meeting.  Story descriptions can sometimes be generalized, so I'm always confirming what he wants out of each story I'm not sure about.  I've learned my lesson from previous communication hiccups where Micah wanted one thing and I created something else.  Communication is key.

Another story not ready for this new iteration is writing some Java code.  More on that next week.

## Ruby Meetup

Our new intern, Brian, Li-Hsuan, and I went to the Ruby meetup.  My last meetup was probably a couple of months ago, so it was exciting to be back and meet new faces and old.  There were a couple of talks that night.  One was on Mongoid, an ODM for MongoDB.  One of the neat features it supported was geospatial 2D querying which reminded me of fuzzy searching.  I don't have a reason for using Mongoid right now, but it seems to be a winner among the Mongo ORM libraries out there.  The second talk was about consumer-driven contracts.  I was only able to get bits and pieces of the talk.  The way consumers and providers work together are similar to how customers and developers collaborate in an agile environment.  Consumers write tests in RSpec or any language and push it to git submodule where the providers run the tests for consumer to make sure features that the providers are providing to the consumers aren't broken in future releases.  If that didn't make any sense, that's pretty much what I got out of the talk, I apologize.  Unfortunately, we had to leave immediately after the meetup to catch the train.

