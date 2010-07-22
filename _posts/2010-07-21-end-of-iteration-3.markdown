---
layout: post
title: end of iteration 3
date: 2010-07-22 10:00:00 -05:00
categories:
  -- software craftsmanship
  -- mongodb
  -- ruby
  -- fail
  -- i18n
---

"Accept that there will be some things that you’re not good at, or that would require a disproportionate investment of time and effort in order to make a small improvement." - Apprenticeship Patterns, [Learn How You Fail](http://apprenticeship-patterns.labs.oreilly.com/ch05.html#learn_how_you_fail)

## Stories Not Delivered

Unfortunately, I was unable to deliver the two stories in Iteration 3.  I assumed I was able to write all possible board states to MongoDB.  If there are 16! possible boards, then the time to write them all to MongoDB would take approximately 150 years.  I will not complete this story in my lifetime.  I should have thought about the problem a bit more than just relying on the little information I already knew.  Since the MongoDB problem took up most of the time, I was unable to complete UI story.  All in all, there were some lessons learned and I hope to better my understanding of the problem.

These stories were pushed to Iteration 4, points were re-evaluated, and another story was assigned.  The new story is about keeping track of wins and losses and displaying them to the user.  This will require another Limelight stage and possibly a new collection in the same MongoDB.

## Internalization (i18n)

The other apprentice, [Li-Hsuan](http://twitter.com/li_hsuan), gave his presentation on [internalization](http://en.wikipedia.org/wiki/Internationalization_and_localization).  It's important that all software development utilize UTF-8 as a standard, especially in this day and age, where more and more countries worldwide, connect to the internet and utilize more applications daily.  He presented several challenges on improper character encoding, improper encoded data in the database, failed multilingual FitNesse tests, and autocompletion feature in a multilingual application.  It was interesting to see the solutions to the problem and to see how some tools do not support internationalization.  

## Pairing with Micah

Later in the day I paired with Micah and I showed him a potential solution to the 4x4 problem.  The board can be rotated and flipped seven different ways and could possibly look the same as the original board.  If I were build the trees for positions 0, 1, 4, 5, then I should be able to get the trees for all board positions.  See below. 

{% highlight text %}
 O | O |   |
---+---+---+---
 O | O |   |    
---+---+---+---
   |   |   |   
---+---+---+---
   |   |   |
{% endhighlight %}

Position 0 should be the same as 3, 12, 15, position 1 should be the same as 7, 8, 14, position 4 should be the same as 2, 11, 13 and position 5 should be the same as 6, 9, 10.  While I only need to build 1/4 of the board, it will still take a long time.  Micah then introduced me to memoization.  I read about memoization in Douglas Crockford's [The Good Parts](http://www.amazon.com/JavaScript-Good-Parts-Douglas-Crockford/dp/0596517742/ref=sr_1_1?ie=UTF8&s=books&qid=1279812995&sr=8-1), but I didn't understand a good use case for it.  The Negamax problem is a great example for understanding the power of memoization.  When implemented, it was nearly identical to alpha-beta pruning.  Memoization takes the redundancy out of the equation.  In the 3x3 problem, alpha-beta pruning made 18,296 moves in the tree on a blank board, then 843 moves in the next, but memoization made 16,167 moves and 7 moves in the next!  Clearly memoization is a better optimization than alpha-beta pruning.  I think I will use the rotating/flipping idea with memoization so I will only have to search 4 positions of a blank board.

I'm glad to have paired with Micah.  Memoization was a great eye-opener and I will blog about the level of optimization it brings to the 4x4 board.
