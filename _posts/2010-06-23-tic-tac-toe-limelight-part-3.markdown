---
layout: post
title: tic tac toe on limelight - part 3
date: 2010-06-23 22:30:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- limelight
---

I spent some more time today studying Limelight and using Micah's hangman example to understand how he created the game.  It's interesting to see how he took the hangman game logic and named it "game engine".  The production then holds an instance of the game engine and a collection of computer players.  Basically, the game engine neatly packages everything there is to the hangman game.  I'm going to somehow mimic the way he designed his code.

I had to re-read the theatre metaphors again to understand how code is structured in a production.  I'm basically digging through the [Limelight RDoc](http://limelight.rubyforge.org/rdoc/index.html), Limelight docs (accessible via ruby -S limelight open command), and the [Limelight wiki](http://limelightwiki.8thlight.com/wiki/Main_Page).  There's a lot to consume and little time left to finish my project this Friday.

Aside the project, last night [jekyll](http://github.com/mojombo/jekyll) updated to 0.6.0 and caused an issue with the syntax highlighting for all of my blog posts.  I [reported](http://github.com/mojombo/jekyll/issues/issue/178/) the issue and fortunately it was fixed by today.  It ended up being the deadly single quote usage for newline escape characters; it should've been double quotes.  If you don't know what jekyll is, it's basically a static site generator in Ruby that is hosted on [GitHub Pages](http://github.com/pages/pages.github.com).  Simply write your blog posts (as I'm doing now) in markdown format, push the new post to your GitHub [repo](http://github.com/sl4m/skim.cc) and watch it instantaneously added to your blog.  It's fun, neat way to publish blog posts than using Wordpress or Blogger.  I highly recommend trying it out.  

Ok, until next time...
