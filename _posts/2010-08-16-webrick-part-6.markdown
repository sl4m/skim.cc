---
layout: post
title: webrick - part 6
date: 2010-08-16 09:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- stories
  -- tic tac toe
  -- WEBrick
---

If you recall, I was having a problem on my WEBrick implementation of Tic Tac Toe where the meta tag hack was showing the board states when Negamax was running.  Negamax was actually causing all sorts of problems because WEBrick servlet was relying on the board's state.  I was able to fix this by modifying the Negamax call to create a duplicate Board class instance when running the Negamax algorithm.  This way it will have no effect on the state of the board in any way.  Other improvements I've made was to prevent hovering of the piece when it was not a human's turn.  This was a simple JavaScript fix that required an additional privatized variable to store the state if the current player was allowed to make click moves.

The try again and quit buttons are now properly displaying on the HTML and work as intended.  I had a problem with the try again button because I had forgotten to reset state for a variable that was being used in session.  The @status ivar was used to identify which image message was going to be displayed (e.g., Player X make a move, Player O is making a move).  I made sure @status reset itself and it seems to be working fine now.  A different kind of problem for the quit button was regarding the thread state which ran the game engine.  I'm still not all too familiar with threading, but when the quit button returned the user to the options page, the game engine thread was still running.  When the user created a new game, a new game engine thread was created.  Somehow this was creating some weird problems I could not identify.  I looked at the rdocs for the Thread class and used the exit method on the game engine thread when the user plays a new game.  I also made sure it only exits if the game engine thread exists.  This seems to have solved the threading issue and I no longer see the anomalies.

Overall, this WEBrick project, while probably the most difficult, was also the most educational.  I learned a lot about how a webserver works (e.g., WEBrick), how much of a headache it can be when dealing with a game engine thread and the webserver, understanding all elements of creating a web application (e.g., HTML, CSS, JavaScript), and the many things you can take for granted when using an awesome web framework like Rails and Sinatra.

I look forward to working on the Rails project.  This will be a fun week.
