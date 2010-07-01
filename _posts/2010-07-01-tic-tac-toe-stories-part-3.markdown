---
layout: post
title: tic tac toe stories - part 3
date: 2010-07-01 18:00:00 -05:00
categories:
  -- software craftsmanship
  -- refactoring
---

Unfortunately, I spent a couple of hours in the morning, fixing an IntelliJ/JRuby issue.  For some reason IntelliJ was not detecting the Limelight gem installed in my JRuby gem repository.  I ended up having to uninstall JRuby via rvm, re-install it, then re-install rspec and limelight gems.

Aside from the environment woes, I continued working on my stories.  Story #7, "Design and build a stunning LL UI with unprecedented usability, animated transitions, and tasteful eye candy" proves to be a challenge.  There's not a lot of documentation on how to animate props, so I had to do some digging in the hangman example.  I was able to piece some code together to animate the pieces displayed on the board.  As each player makes a move, the transparency level is changed from 100% to 0%.  Neat.  The next thing I want to work on is a way to display the player's piece over an empty space when the user hovers over it.  The piece will be in a semi-transparent state.  I still have a ways to go with this story as the customer requested four other items:

* small exit button
* hide others controls during a game
* no square board layout, but hash
* display a strike-through for wins, display something "cool" for draws

I'm also thinking about how I'm going to implement a 4x4 board option.  This is not going to be an easy task because there's a lot of changes that need to take place in code.  This probably indicates my code was not designed very well.  Here are some of the items I brainstormed that need to be changed:

* Some unit tests hard-code the board size
* Limelight UI hard-codes the board
* Add option for 4x4 board to all UIs
* MinMaxPlayer class's minmax algorithm
* Board class's winning method

This is probably going to the most difficult to implement.  I still have problems with my 3x3 minmax algorithm, I'm not sure how I'll tackle the 4x4 minmax algorithm.

I added missing unit tests to test the mouse_clicked event which I now know how to test.  I will work on story #7 some more tonight and continue brainstorming about the 4x4 board.
