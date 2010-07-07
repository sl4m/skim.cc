---
layout: post
title: tic tac toe - iteration #2
date: 2010-07-07 10:30:00 -05:00
categories:
  -- software craftsmanship
  -- refactoring
  -- meetup
---

*Note:* The holiday weekend and yesterday's Chicago Ruby meetup is throwing me off a bit on the blog posting.  I should return back to normal schedule by today.

Yesterday marked the first day of Iteration #2 for my Tic Tac Toe program.  As you might have read from the previous post, I was able to get the alpha-beta pruning working.  Now that I have a couple of algorithms developed, I'm going to look into using the [Strategy Pattern](http://en.wikipedia.org/wiki/Strategy_pattern) and extract out the algorithms from the MinMax Player.  I'm also going to use [Rename Method refactoring](http://en.wikipedia.org/wiki/Rename_method) to rename MinMax to Negamax.  I'm already confused as it is with the names, so I think this will "better reveal its purpose."

I signed up for the Chicago Ruby meetup, so it was a short day.  [Eric](http://twitter.com/paytonrules), swapped craftsman, [Rob](http://twitter.com/rsanheim), and I took the train down to Chicago.  

The two talks were about HTML5 + websockets and contributing to open source.  The latter resonated with Ryan Bates' [Give Back to Open Source](http://railscasts.com/give_back) as well as a touch on software craftsmanship.  One idea I took from [Blake Smith's](http://twitter.com/blakesmith) talk was about using 

{% highlight text %}
git log
shift+g
{% endhighlight %}

on a certain git repo to look at the author's first commit.  You can then see what the person did to improve the code.  Blake also listed some strategies to welcome maintainers for projects:

* Asking the person to create a patch for the problem
* Create contribution guides
  * list gem dependencies
  * how to run tests
  * acceptability guidelines
  * submitting the patch
* Words of encouragement

After the meetup, a group of us headed down to Elephant and Castle.  It was great to see familiar faces I usually see in Twitterverse - Dave Hoover, Corey Haines, and getting to know other Rubyists in Chicagoland.  I hope to attend more meetups as time permits.
