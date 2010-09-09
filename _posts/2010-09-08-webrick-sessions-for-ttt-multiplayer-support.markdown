---
layout: post
title: webrick sessions for ttt multiplayer support
date: 2010-09-08 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- tic tac toe
  -- webrick
  -- rails
---

## Pairing with Micah

Micah and I paired towards the end of the day working on the story to allow multiple players play Tic Tac Toe games on the same web server.  We first did a bit of refactoring on the Board class to remove a smelly argument list for initialize method and added some class methods to be called in the story.  Then Micah created a nice, lengthy RSpec test which mocks cookies and params coming in from the request and verifies that the game is resumed (WEBrick is now creating new servlet instances), makes a move (using the params value), and stores the new board state, board, and players into the request.cookies array.  Of course, since we ping ponged, I wrote the feature, but it was a really nice exercise.  Pair programming really helps me be more engaged than trying to figure out the problem alone.  It was really nice to be able to bounce ideas around, get assistance for a good number of errors I wrote in, and mostly learn from the other person.  Now that Micah gave me a great boost to this story, I should be on my way to complete this by tomorrow.

## Web Heresies

I read a great [article](http://www.windley.com/archives/2007/03/applied_web_heresies_etech_2007.shtml) about Avi Bryant's talk on the need to re-evaluate design decisions that were unconsciously adopted into modern web frameworks.  The [slides](/files/etech_heresies.pdf) go through an example to create a simple web application using recipes from Seaside:

* Justification
* Inspiration
* Implementation
* Re-implementation
* Omissions

Although, the talk is several years old, it was an interesting exercise to go through and to see how WEBrick can be used to serve custom procs rather than the servlet templates WEBrick offers.  While I didn't have time to re-implement my WEBrick piece for Tic Tac Toe, it'll be interesting designing it the "Seaside" way.

## Rails 3 on Windows is Hard

As said previously, I coined the idea to develop the Rails 3 app on the Windows platform and I tried to get started tonight.  Unfortunately, I ran into issues with Bundler and the IDE (RubyMine), so I gave up for the night.  I'll try again and see if I can passed them.  Another issue, not platform related is the issue of including the Tic Tac Toe game engine library without duplicating it.  I may finally throw it in a gem include it in the Rails project.  I'll have to see...
