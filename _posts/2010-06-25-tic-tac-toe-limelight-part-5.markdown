---
layout: post
title: tic tac toe on limelight - part 5
date: 2010-06-25 23:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- limelight
---

Today I paired with a couple of people for my Tic Tac Toe project.  It's open door Friday again and I first paired with Jason who came to visit from Nielsen (media ratings company).  It was really great to have him dissect the problem with me because we were clearly able to identify the root of the problem.  The way my program is designed now, TicToeToe and Game classes are responsible for these "pseudo event" loops.  When integrating Limelight UI into the mix, the responsibility of the event loop changes.  It's the Limelight framework that handles the event loop.  So basically what I need to do is change the way my code is written to have my stdin/stdout UI class be responsible for the "pseudo event" loops.  I also paired with Matt Hinger, an 8th Light intern who developed the game, [Quixo](http://github.com/mhinger/Quixo2), last summer in Limelight.  I asked him many questions on certain things that I didn't understand about Limelight and he was very helpful.  I'm going to take a look at his source code to see how he implemented certain things.  I guess props in Limelight do not have a visible attribute, so Matt ended up sizing them to zero to essentially make them inaccessible to the user.  I think a combination of the transparency and disable attributes will achieve the same thing.  I'll have to test it out.

This is the last day for [Anders](http://twitter.com/unders), so for lunch we had him talk briefly about [Elabs](http://elabs.se/) and how they work, followed by answering questions we had.  One notable question was about "permanently" pairing in projects.  I think Elabs pairs by default, but at 8th Light, we pair when we ask others to pair.  Micah replied that he does not want to mandate pairing, but opens it up for people who want to pair in the beginning, or middle of a project.  There's something to be said about pairing in situations where you won't get the most benefit out of it (e.g., simple tasks).

After lunch, as part of a quarterly tradition, Micah briefly talked about re-arranging the office layout.  There are certain "rules" to this tradition:

* it cannot be the same layout as before
* all things on desks were to be removed and desks were to be sprayed down and cleaned

Micah then asked for "foreman" volunteers who were in charge of each side of the floor and we went from there.  I think this is a great tradition.  Not only are the 8th Lighters working together, but also the feeling of change is in the air.  I think change prevents a rigor mortis like energy in the office and it feels like a new place.  Not to mention the weather today was as gorgeous as it's ever been.  This was a great day to end the week.
