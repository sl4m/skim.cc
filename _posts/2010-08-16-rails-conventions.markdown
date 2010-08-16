---
layout: post
title: rails conventions
date: 2010-08-16 18:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
---

Today was the first day working on the Rails app.  Matt and I pair programmed using iChat screen share to take turns moving around the application code to learn more about it.  My lack of using certain tools prevented us from rapidly progressing forward today.  We needed to ssh into the client's staging server to pull down a backed up database so we can use it locally.  Then we needed to figure out how to create a user so we can log in to the test application.  Fortunately, Craig and Paul were helpful and guided us in the right direction.  There was an issue we discovered that appended post form data parameters to the end of the response URL without a question mark which caused a Rails routing error.  Fortunately, it was not a problem on our side and as a workaround, we'll add the question mark to the URL.

I must say, I enjoy the Rails conventions, but it does have a small learning curve when you're rapidly learning and developing Rails.  I'm sure as I continue, the conventions will be second nature, as they should.  

I plan to look at the application code some more tonight and read the [RailsGuides](http://guides.rubyonrails.org/getting_started.html).  We're having a stand-up tomorrow, so I should have an estimate of how long this implementation task is going to take.

## ChicagoDB Meetup

This will my first attendance at the [ChicagoDB meetup](http://gathers.us/events/chicagodb-august-meeting).  It's going to be at the Hashrocket office and I look forward to meeting Chicago Rubyists I haven't met yet.  The topics include Google's MapReduce and CouchDB.  Look forward to learning about those NoSQL databases and my only experience thus far has been with MongoDB.
