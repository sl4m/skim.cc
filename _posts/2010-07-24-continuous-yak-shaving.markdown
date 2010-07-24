---
layout: post
title: continuous yak shaving - lessons learned
date: 2010-07-24 12:00:00 -05:00
categories:
  -- software craftsmanship
  -- mongodb
  -- ruby
  -- yak shaving
---

This was a wonderful week of yak shaving.  Experimenting with MongoDB, memoization, memory allocation optimization, score randomization, all while in a <strike>recursive</strike>, <strike>recursive</strike> recursion, led to some important lessons learned.

## Continuously run your tests

Your tests are there to help you understand if the changes you've made in the code broke existing functionality.  When introducing memoization, memory allocation optimization, score randomization to my NegamaxPlayer class, I failed to add and test them individually.  The course of action I should have taken:

1. Write the test for new method
2. Run the test, see it fail
3. Add code for new method
4. Run the test, see it pass
5. Run the entire test suite
6. Commit changes
7. Repeat Step 1

## Start with a clean slate, if your tests are failing

Sometimes, when you're knee deep in your newly written code, the tests aren't passing, and you're getting super frustrated, it's best to start over.  After a long day of attempting to fix tests and frustration ensued, I ran the wonderful command *git checkout -- file* and started over.  I added the new methods individually and made sure each method passed all tests before moving on to the next.  Seeing green once again put me in a really good mood.

## Truly understand how algorithms work

I know this sounds obvious, but while working on the Negamax algorithm code, I sometimes get lost inside the recursion (I think I need to read [The Little Schemer](http://www.amazon.com/Little-Schemer-Daniel-P-Friedman/dp/0262560992).  On any given day I'll understand how it works, but there are times when I'll forget and won't quite understand it.  Without truly understanding the algorithm, I'm at a disadvantage and solving problems for it can be difficult.  I know since last month when I started working on it, I have a much better understanding of the algorithm.  I'm not quite sure how to improve my understanding of it, except by reading the code everyday.  I guess it's just a matter of time.

## Use your math skills, estimate completion time

When working on storing all possible 4x4 board states in MongoDB, I failed to calculate how long it will take for me to store the moves to the database and if the generated board states were redundant.  After running the code for about a day, I calculated the completion time to be about 150 years which in no way was going to be finished...in my lifetime.  Had I calculated before running the code, I could have saved A LOT of time.  I think I've lost a total of 4 days by not using simple math skills to understand the root of the problem.  This was probably one of the hardest lessons learned.

## Work on one story at a time, perform commits frequently

This was part of my [retrospective](http://skim.cc/2010/07/08/tic-tac-toe-iteration-2-part-3/) for Iteration #1, but it needs to be said again.   I tend to work on a story, leave it uncomplete, and work another story.  When I attempt to go back to the first story, I don't remember what I did, worse, I don't remember how to fix the failures that were introduced from before.  Of course, everyone works differently, and some will be able to leave unfinished stories behind and work on them later.  As I learn the ropes, I think the best way to manage is to work on them one at a time.  If I'm working on a story, I'll break it down to smaller tasks and commit frequently.  Or if the story can be broken down into multiple stories, I can work on one, break it down to smaller tasks and commit frequently.  One of the 8th Lighters told me he likes to have a story anywhere from 1-3 points.  Anything higher and he breaks them into smaller stories.  I think when stories are kept small, they're easier to manage and rewarding when you completed them.  Having one big story staring at you in its incomplete state can be daunting and frustrating.

## Conclusion

There were some good lessons learned this week.  I can't say I'll ever stop yak shaving, but with time comes discipline and hopefully less yaks will need to be shaved.  Happy weekend!
