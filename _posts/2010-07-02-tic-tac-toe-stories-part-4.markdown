---
layout: post
title: tic tac toe stories - part 4
date: 2010-07-02 22:00:00 -05:00
categories:
  -- software craftsmanship
  -- refactoring
---

*Note:* In my previous posts, I called 8th Light's Fridays, "open door Fridays" where in fact it's actually called "Lunch 'n Learn".  

It was my turn to pick up lunch for Lunch 'n Learn (Li-Hsuan and I switch every week), so I was a bit occupied in the morning.  [Eric Smith](http://twitter.com/paytonrules) continued with the OpenGL class and touched on perspective projections, rotations, matrices, and more.  Some of it is still over my head, but I think a little bit of reading in the tutorials [here](http://nehe.gamedev.net/) will yield some good information.  Our homework assignment due next Friday is to:

* take our existing model and render it using perspective projection
* make more than one appear on screen in different places, sizes, rotations
* bonus points if animated

Last night and throughout part of today I worked on my minmax algorithm.  I thought my algorithm code was broken, but it actually isn't.  One thing is pretty clear, my MinMax player cannot be beat.  But when the winning opportunity is given to the MinMax player it won't take it - at least not right away.  The problem lies around the issue with depth and scoring.  While Eric was giving his presentation, I had one of those aha! moments and tweaked my scoring method to give a better score for a move that had an immediate win than a score without.  This is a rough look of the new scoring method:

{% highlight ruby %}
  def evaluate_score(board, piece, depth)
    opponent = get_opponent(piece)
    case board.winner
    when piece
      return (depth == 2) ? 2 : 1
    when opponent
      return (depth == 2) ? -2 : -1
    else
      return 0
    end
  end
{% endhighlight %}

With this update, the two new test cases I wrote that used to fail, now pass.  Next week, I'll need to implement [alpha-beta pruning](http://en.wikipedia.org/wiki/Alpha-beta_pruning) for performance and implement the randomization of the set of mirrored moves.

I continued working on Story #7 and implemented an animated eye candy piece when a player wins.   Using the hangman example, I created an animation which changes of colors for the winning row.  This required a new method in the Board class which will store the winning row in an array.  Then the Limelight default scene will take that winning row and set it to the colors of the rainbow, in an endless loop until a new game or exit of game.  I wanted to show you what it looked like, but I'm afraid I don't know how to create gifs on the Mac.  You'll just have to clone the repo when I push the new changes to it.  I plan to implement the rest of Story #7 items over the weekend.

This weekend is the Fourth of July weekend, and I plan to go down to the city for the first time since I moved here.  I'm particularly excited to see The Sight Below play at Empty Bottle this Sunday.  I hope his set is as good as the [one from Seattle](http://soundcloud.com/modyfier/the-sight-below-process-part-200-live-at-the-seattle-art-museum).
