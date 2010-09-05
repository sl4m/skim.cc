---
layout: post
title: game change
date: 2010-09-04 17:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- tic tac toe
  -- webrick
---

Yesterday, I paired with Micah to go over the problem I was having about handling WEBrick servlet instances and sessions.  He asked me great questions when I told him about the problem in detail.  One obvious problem when removing the Singleton pattern in the servlet class is the fact that the web server will instantiate a new servlet for every GET/POST request, therefore state was no longer persisting.  The game engine requires an instance of the UI and I used the servlet as the UI.  Instead of using the servlet, I could abstract the UI methods in the servlet into a new UI class and create an instance of that.  I may not be thinking this through clearly, but this might work.  

The real underlying problem is the game engine running in a separate thread.  Threads can be complicated and hard to work with, especially if you don't know what you're doing.  I introduced a thread in the Limelight version of Tic Tac Toe and for the most part, it's been working without problems.  It's a whole different game (no pun intended) when introducing threads in a web environment.  It doesn't quite work the same.  The game engine is unable to magically report back that the computer made its move and update the web page.  I'm currently using what I call a hack where the meta tag refresh the page which calls the GET request every two seconds.  Micah quickly spiked a method called "non_blocking_play" which only runs when it's the computer player's turn.  I'll have to somehow implement the human player's side and have it work with both Limelight and WEBrick implementations.  Micah also brought a neat way of using the cookie.  I could store the board state inside a cookie and have the servlet resume the game.  I don't currently have a way for the game to resume, but I don't think it'll be too difficult to support.  This way the server does not have to hold instances of the game for every player and I can lose the Singleton pattern.

## TODO List

* lose the Singleton pattern => servlet should not be persisting state
* lose the thread implementation
* create a Session class to hold all sessions on server side (for now)
* later implement a way for game to resume and store board state in cookie
