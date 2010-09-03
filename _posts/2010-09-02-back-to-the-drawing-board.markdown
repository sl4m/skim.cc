---
layout: post
title: back to the drawing board
date: 2010-09-02 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- tic tac toe
  -- webrick
---

## WEBrick woes

It looks like my idea of combining the instances of the servlets paired with cookie sessions failed.  Unfortunately, I could not figure out how to get the request prior to the instantiation of the servlet.  The request has the array of cookies stored for the browser.  I was unable to access the cookies therefore I was unable to return the instance tied to a cookie id.  Drats.  

So I tried a different approach.  I tried storing the sessions in the servlet, remove the Singleton pattern, and retrieve the session by cookie id during a do\_GET and a do\_POST.  The do\_POST method is called when the user submits the game options.  The do\_GET method will be called during the rest of the game to get user's move as well as the computer's move via meta tag refresh hack.  Since these methods are the only entry points to the servlet, I thought having the servlet handle the sessions would work.  Except I forgot about one minor detail.  The game object has an instance of the servlet (ui) object and sends messages to it on a different thread.  Unfortunately, since I removed the Singleton pattern, each servlet triggered by GETs and POSTs will create a new instance of the servlet.  This is just the way WEBrick works.  Since it's creating a new instance, the game object no longer has the correct servlet object and it blows up on runtime.  At this point, I'm not sure what to do next.  This is my first time reading/writing to cookies.  I might have the whole concept of cookies wrong, so I plan to research it more tomorrow.

As for the other story, "Persist player records", I thought about using MongoDB to persist the scoreboard scores, but decided against it to avoid writing a failsafe when MongoDB does not exist on the machine.  CSV was the simple answer and I was able to implement it right into the Scoreboard class.  Before, the Scoreboard class created a new hash for both players ('O', 'X').  Now it will read from the csv and write to the csv when Scoreboard\#add_score is called.
