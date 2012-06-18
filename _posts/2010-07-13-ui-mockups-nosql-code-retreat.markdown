---
layout: post
title: ui mockups, nosql, code retreat
date: 2010-07-13 22:45:00 -05:00
categories:
  -- software craftsmanship
  -- ux
  -- nosql
  -- design and principles
  -- code retreat
---

## UI Mockups

I met with the customer today to go over the UI mockups and overall he seemed happy with them.  I need to add a Try Again yes/no overlay on the board and add tasteful images to the board and pieces.  He still wants an unprecedented, eye candy look to the game, so if I can't find any Creative Commons images on the web, I may have to create them from scratch using an image editor.  I wonder if I can make the board and pieces look 3D.  I'll have to do some research.

## Breaking Open/Closed Principle

When I showed Micah (mentor) the 4x4 board option, I explained to him about the 4x4 complications of the regex pattern matching for the CpuPlayer class.  He indicated that the EasyCpuPlayer and NegamaxPlayer can be extensible ([open/closed principle](http://en.wikipedia.org/wiki/Open/closed_principle)) when changing things like supporting a 4x4 board, but the CpuPlayer cannot.  I'm not sure if there is a way to make it extensible (e.g., throwing the patterns into a module and including it in CpuPlayer) or if pattern matching is just not the way to go.  Either case, it still tries to win/block when it sees the pattern and is code-wise, better than the EasyCpuPlayer.  I have spare time to put effort into the performance of the Negamax against the 4x4.

## NoSQL for Negamax

I told Micah (mentor) that it takes the Negamax player approximately 68 minutes to make its first move.  He asked me if I knew ways of improving the performance and hinted that the NegamaxPlayer is repeating itself every game.  I thought storing it in a database didn't work when Colin recently talked about his solution.  I got it all wrong, however.  Building the index and writing the possible moves to the database took the longest.  When playing the game, however, the lookup was actually really quick.  Since [NoSQL](http://en.wikipedia.org/wiki/NoSQL) is the rage these days, Micah wanted me to spike and look into using a NoSQL data store.  Awesome!  What a great way to experiment with non-relational data stores!  I have some experience reading/writing to relational databases, so it'll be interesting how non-relational data stores work in comparison.  Of the NoSQL data stores out there, [Redis](http://en.wikipedia.org/wiki/Redis_(data_store)), [CouchDB](http://en.wikipedia.org/wiki/CouchDB), [MongoDB](http://en.wikipedia.org/wiki/MongoDB), and [Cassandra](http://en.wikipedia.org/wiki/Cassandra_(database)) were mentioned by some 8th Lighters who have used them.  I think I'm going to use CouchDB or Redis.  I hear MongoDB an awful lot in Twitterverse, but the 8th Lighter who has experience using it is on vacation.  Rats.  From the spike, I should have an understanding of what data store to use.  More on that later.

## Code Retreat with Corey Haines

Corey stopped by the 8th Light office and guided us on a session of his code retreat.  It's the original code retreat that [inspired the code retreat sessions](http://skim.cc/2010/06/09/day-2-railsconf-2010/) I participated at BohConf (at RailsConf) this past month.  We all paired up and TDD'd to our heart's content in an attempt to create Conway's Game of Life.  Here are some notes I wrote down from the session:

* don't immediately jump to abstractions
* create smaller scopes
* test like breathing
* reveal intent
* create smallest test/code possible

The code retreats are about minimizing the gap between what you wish you could code and what you actually can code within a given time.  The gap is how much you suck.

At the end of the session, we threw away our code in a habitual effort to detach ourselves from the code.  I'm going to try these code retreat sessions for the [Game of Life challenge](http://rubylearning.com/blog/2010/06/28/rpcfn-the-game-of-life-11/) and see where it leads me.
