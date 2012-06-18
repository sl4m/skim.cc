---
layout: post
title: rails 3 and new iteration
date: 2010-09-14 23:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- tic tac toe
  -- rails
  -- java
---

## New Iteration

Micah and I went down to the Chicago office because he had a meeting with a client.  We had the end of iteration meeting in the afternoon, and unfortunately, I did not complete the Rails 3 Tic Tac Toe in time.  I was stuck trying to figure out why the game engine library was not loading automagically (Rails convention) when copied to the lib directory.  It kept giving me uninitialized constant error messages.  Once I have that figured out, I just need to change the erb files from the WEBrick project, tweak things here and there and it should be ready to go.  I'm really hoping for a 2-point story.  It should optimistically take half a day to do.

Since I missed this iteration and some in the past, Micah sent me a spreadsheet to better estimate my stories.  It uses [PERT](http://en.wikipedia.org/wiki/Program_Evaluation_and_Review_Technique) estimate calculation.  PERT stands for Program Evaluation and Review Technique and was used by the U.S. Navy in the 1950's.  Instead of giving one estimate for a story, you give three:

* Optimistic Estimate - if absolutely everything went according to plan
* Realistic Estimate - real world, greatest chance of success 
* Pessimistic Estimate - wildly pessimistic, all wild obstacles included

With these estimates, it'll calculate the true estimate based on this formula:

{% highlight text %}
(O + 4R + P) / 6
{% endhighlight %}

This will calculate the mean and it rounds to the nearest point.  For example, I said one particular story has an optimistic estimate of 2 points, realistic estimate of 3 points, and pessimistic estimate of 4 points.  The mean for these estimates come out to 3.  This is my estimate for that story.

Hopefully, this will aid me in providing accurate estimates for the stories.

## What's New in the Next Iteration

Last week, I said I will be working in the Java language.  Here are the new stories for this iteration:

* write a telnet server in Java
* write the Sieve of Eratosthenes in Java

The Rails 3 Tic Tac Toe story is part of this iteration as well.  I'm excited to be learning a new language.  I took a Java class a while back and familiarized myself with the language.  Hopefully, I'll be able to recall most of the information.  I'm also borrowing Effective Java from the 8th Light library, so I'll need to do some reading this week.  
