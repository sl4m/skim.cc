---
layout: post
title: storing 4x4 on mongodb - part 3
date: 2010-07-23 11:00:00 -05:00
categories:
  -- software craftsmanship
  -- mongodb
  -- ruby
---

I'm back to storing 4x4 possible board states to MongoDB.  If you recall from the [previous](http://skim.cc/2010/07/22/end-of-iteration-3) [posts](http://skim.cc/2010/07/20/storing-4x4-on-mongodb-part-2), I spent days working on what I thought was the solution, when in fact I was attempting to store trillions of board states which contained a lot of redundancy.  I removed alpha-beta pruning and added memoization using MongoDB to read/write board states and its respective best scores.  The best thing about using memoization and MongoDB is that if I were to stop the method, I won't lose the work it has previously done.  I can stop and resume at any time.  I'm in the process of optimizing the Negamax algorithm; Micah pointed out that my code was creating new arrays at each recursive call which allocates memory for each array.  Instead of creating new arrays for every board, I plan to "undo" the board move when it's completed the score for that move.  This should speed things along.  It's been running almost half a day and has only stored ~310,000 board states vs. the ~130 million it used to store.  It's either running a lot slower than the previous algorithm or there's a lot of redundancy.

I'm also in the process of making my RSpec tests pass again.  When I was working on the UI story and changing the GUI around, my tests that were looking for those GUI fields started to fail.  I have a bad habit of leaving a story and working on another and not remember what I did in the previous story.  I plan to focus my time today to fix these failing RSpec tests.
