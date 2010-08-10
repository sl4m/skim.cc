---
layout: post
title: webrick - part 4
date: 2010-08-09 20:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- webrick
---

I made some small breakthroughs today on WEBrick.  First, I figured out how to make moves using the image based links.  Simple enough, the links return back to the BoardServlet via GET.  Now I just need to figure out a way to block the user when it's the computer's turn.  I guess I won't know until I get to that point, but it's a good starting point to the story, "Allow the user to click on a square to make a move."

I scoured the interwebs again to find information on WEBrick and I ended up finding some good articles.

* [GET/POST dump](http://ttripp.blogspot.com/2007/01/fun-with-http.html)
* [Running Servlets with WEBrick](http://codeidol.com/other/rubyckbk/Internet-Services/Running-Servlets-with-WEBrick/)
* [Basic WEBrick setup](http://snippets.dzone.com/tag/webrick)

From these articles, I keep noticing the Mutex class being used to handle multithreading situations.  I put the synchronize code block in my code, but I'm pretty I won't run into the problem.  Inside the synchronize block, however, I'm going to need.  See [here](http://gist.github.com/516463) (since pygments is giving me a hard time with this code).

What I found out through trial and error is that on every refresh, a new servlet instance is created.  Since a new one is created, the old one is lost and I'm no longer able to keep track of the game state.  I've not ever used class instance variables before and I've not so good things about it.  However, I can't think of a better way to resolve the problem (and without using global variables).

As you may know, WEBrick documentation is a bit scarce.  WEBrick's own [website](http://webrick.org/) seems to be down and the latest documents on the web date back to 2004.  I realize WEBrick development is dead and most libraries that utilize WEBrick provide the convenience of not having to know the details of how WEBrick works, but I wish there was good documentation.  Then it hit me.  Why haven't I thought of this before?  The WEBrick library is just a Ruby library.  I can just look in there.  So that's where I am now.  

There are several roadblocks which are preventing me from working through the story "Web design should conform to Limelight design.  It should look almost identical."  One of the roadblocks is trying to serve an ERB with references to CSS and the background image.  For some reason, it cannot find the files.  I tried providing it a full path, path relative to the current working directory, return the path via method call in ERB - I feel like I've done everything to no avail.  What seems to work as of now is to read an rhtml file, run ERB, and spit it back out to an html file.  Unfortunately, after that I have no control since the DefaultFileHandler servlet takes over.  I'll have to do more research on this...  


