---
layout: post
title: return of tic tac toe on rails 3
date: 2010-10-04 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- yak shaving
  -- ruby
  -- stories
  -- tic tac toe
---

From [The Craftsman 62, The Dark Path](http://thecleancoder.blogspot.com/2010/10/craftsman-62-dark-path.html):

> "It's not so much choosing the right tests, Alphonse; it's about realizing that you are trying to solve the wrong test." 

If you recall from a previous blog post, I did not write tests for my Rails 3 version of Tic Tac Toe, so I'm re-writing it TDD style.  I should have known better to write tests.  Most of the code was a straight copy from my WEBrick version, so I thought it did not need to be tested, but there were some things that were modified to work in Rails that should have been tested.  For instance, I had ditched my own config class for Rails config and moved all UI methods into the controller.  Instead of moving the methods to the controller (it should not belong in there), I should have "moved" them to the model and test drive from there.

## Game Engine - No longer duplicated

For the longest time, I was trying to figure out how to make the same game engine that worked for all UIs, work for Rails 3.  I thought about creating a gem and eventually went with the idea of just copying the game engine into the lib directory, but that in it of itself is a smell.  Today, I'm happy to say the game engine is one again.  This probably goes against Rails convention, but the Rails 3 project points to the game engine that is not within the project.  The game engine sits happily outside on the same level as the Rails 3 project.  I created a namespace, TicTacToeEngine and wrapped the module name around all classes.  So the directory structure looks more gem-like (e.g., tic\_tac\_toe\_engine.rb and tic\_tac\_toe\_engine directory).  Through this process, I discovered I was able to keep the config class and used it instead of Rails 3 config which is simply a global constant anyway.

## Re-visiting MVC architecture

Michael Hines puts it nicely by saying the following in his [blog post](http://blog.michaelphines.net/traditional-mvc-the-model-is-not-an-active-re):

> In MVC the role of a model is to maintain the domain logic. The role of the view is to make the model easy for the user to understand and match his mental state. The role of the controller is to respond to events by telling the view and/or the model what to do with that event. It’s not the controller’s job to know how to do it, though.

My Game controller knew too much by knowing how to do the job of running Tic Tac Toe.  It really should be the model that knows how to do the job.  Colin mentioned this as well that he usually places domain logic inside models.

## CSV is evil, YAML to the rescue

I had an issue running the console version of the game via Ruby 1.9.2.  It had something to do with the changes made to CSV class.  I'm not sure why I didn't think of this sooner, but I scrapped CSV for the simple-to-use YAML.  Having since used YAML in Rails projects, I knew this was alternative to the evil CSV.

## To be continued

I still need to test drive the model, but I should be good to go for the deadline.  More on that tomorrow.
