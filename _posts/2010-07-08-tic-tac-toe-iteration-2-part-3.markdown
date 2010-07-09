---
layout: post
title: tic tac toe - iteration 2 - part 3
date: 2010-07-08 20:30:00 -05:00
categories:
  -- software craftsmanship
  -- refactoring
  -- retrospective
---

*End of Iteration Meeting*

This is part 3 of what I thought was Iteration #2, but today officially started the new iteration.  Micah (customer) and I had the "end of iteration" meeting today where we went over the stories that were allotted for Iteration #1.  I've managed to complete all of them plus more from the backlog; but this iteration lasted for more than a week due to the holiday and scheduling conflicts.  With that said, I'm right around the ballpark of 10 points per week which is what 8th Lighters complete.  I moved the completed stories to the archive as I demonstrated and talked about each one.  Micah was satisfied with almost all of them except for the Limelight UI enhancement story which I did not meet his expectation (more on why in the retrospective below).  However, to improve on that story and to improve my designer eye, we created a story that calls for creating a mock-up of the game UI from a designer point of view using [Balsamiq's Mockups](http://www.balsamiq.com/products/mockups/desktop) application.  I look forward to working on this story as I could use some designer experience.

The other big story (5 points) is to have the option of playing a 4x4 Tic Tac Toe board.  I estimated the story at 5 points because of the changes I'll need to make to the existing classes:

* UI classes
  * ask user for the board type
* Board class
  * display 4x4 board
  * add winning patterns for 4x4
* CpuPlayer class
  * rules-based logic to support 4x4

Initially, I thought I needed to create a new Negamax algorithm for the 4x4 board support, but after looking at the code and thinking it through, it's not needed.  The Board class will know when the game is over from a draw or win.

I am to complete these two stories by the end of this new iteration.

*Retrospective*

This was my very first [retrospective](http://en.wikipedia.org/wiki/Retrospective#Software_development) ever.  I think retrospectives are a way of saying "Hey, I care about you and your quality of work, let's do something about continually improving what you do."  It's a great feedback loop between customer and developer to reflect on the good and bad and come up with ways to improve for the next iteration.  Here is the list of good and bad we came up with:

* \+ tackled small stories first
* \+ stories were completed
* \+ some stories from backlog were completed
* \- working 24/7 
* \- weekend broke productivity flow
* \- mismatch expectation for Limelight UI story
* \- lost in refactoring tangent
* \- not throwing away spike code

Although there were more bad than good, I think having them exposed can help us confront them rather than not talking about them at all.  This is what we came up with to improve the bad:

* working 24/7
  * work less
* weekend broke productivity flow
  * perform smaller commits
  * complete task at hand or leave failed test to act as a bookmark
* mismatch expectation for Limelight UI story
  * more communication with customer during iteration for quick feedback loop
* lost in refactoring tangent
  * discipline over time
* not throwing away spike code
  * throw it away

We didn't really talk about "working 24/7", but in practical sense, I should work less.  If I burn myself out, I'll end up losing more time, recovering, than the extra amount of work completed from the late hours.  While there will be some weekends where I'll need to catch up on stories, etc., weekends should be about me.  Lately, I've been continuously learning almost every evening and weekend to learn as much as I can.  This was my choice though, but I hope to find a good ratio of work, study, and play.  Maybe a retrospective about continuous learning?

Communication is important between customer and developer and the mismatch expectation was a result of poor communication on my part.  I should have ask the customer if the Limelight UI enhancements I made were what the customer expected early on instead at the "end of iteration" meeting.  I know better for next time.

*Motivation*

This was the last day for swapped craftsman, Rob, so he gave us a work-in-progress talk about motivation.  This was similar to what I read/[watched](http://www.ted.com/talks/dan_pink_on_motivation.html) from Dan Pink.  I look forward to picking up Dan Pink's book [Drive](http://www.amazon.com/gp/product/1594488843/ref=ord_cart_shr?ie=UTF8&m=ATVPDKIKX0DER) and a recommended book from the talk, [Flow by Mihaly Csikszentmihalyi](http://www.amazon.com/gp/product/0061339202/ref=ord_cart_shr?ie=UTF8&m=ATVPDKIKX0DER).  Apparently, [Relevance](http://thinkrelevance.com/) implemented [20 percent time](http://googleblog.blogspot.com/2006/05/googles-20-percent-time-in-action.html) which allows them to work on projects that contribute to their business.  I hope to see something like this implemented at 8th Light.
