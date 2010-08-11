---
layout: post
title: webrick - part 5 
date: 2010-08-10 20:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- webrick
---

I made some good headway on the WEBrick stories today.  I dove into a bit of JavaScript to create a mouse over/out effect - it will show the user's piece over an empty square.  There is some passing of information between the servlet and JavaScript functions.  Seeing as I've never done this before, I basically created a closure in JavaScript to hold a privatized variable where I can set the current player.  The mouseOver and mouseOut functions use this variable to display the proper image of the piece.  There's probably a better way, but this seems to work.

I continued working on the game engine side of the project, transferring a lot of similar code found in my Limelight project.  I'm going to have to come back and extract these duplicates and create a shared module of some sort, but for the sake of completing these stories, it'll have to do.  Most of everything is in place, except I'm having a bit of trouble getting the computer to communicate to the WEBrick UI that it's made its move.  If you recall, the game engine is running in a separate thread so it can run independently from the UI.  Through the Limelight Hangman example, I was able to work through a solution for the Tic Tac Toe on Limelight.  However, in WEBrick, I'm finding it difficult to send GET requests programatically.  Maybe it's my lack of GET/POST knowledge and lack of web development overall, but this is where I'm stuck on.  I could temporarily have the computer make its move during the human player's GET process, but in a situation where two computers goes head to head, the page will never be refreshed.  I may look into Ajax for a solution.  Anyway, I plan to work on this more tonight.  Hopefully, I'll see the light on the other end.

Here's what I have so far:

![TTT WEBrick Draft](/images/ttt_webrick_draft.jpg)
