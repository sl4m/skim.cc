---
layout: post
title: http server in java - request and response
date: 2010-10-11 17:00:00 -05:00
categories:
  -- software craftsmanship
  -- yak shaving
  -- java
  -- http server
  -- apprenticeship challenge
---

I'm happy to say the HTTP server is complete.  There were some gotchas as Micah said late last week, but when seeing an index page load up for the first time last night, I was super excited.  When was the last time you were excited when a web page loaded successfully?

## HTTP Request and Response

I've implemented the HTTP Request and Response classes.  The Request class was straightforward.  It reads the request from the socket's InputStream.  Fortunately for GET requests, the request byte size is small (roughly 500 bytes), so I do not need to do some sort of checking.  If it were a POST request, my max BUFFER\_SIZE of 1024 will not be sufficient.

The Response class was where all the work was done.  Once the Request class has parse the request and identified the URI path and parameters, it's the Response class job to write a response to the client.  First, it checks to see what the client is asking for.  If you recall, my HTTP Server was to do the following:

* serve static pages
* when visiting /hello off the root, it will display any parameters if found
* display 404 Not Found for anything else

The URI path coming from the Request does a nice job of identifying if the URI path is without a file name.  If so, it attempts to add /index.html and check to see if the file exists.  If it does, then it's added as part of the URI path, otherwise left alone.  The Response class will use this information to determine if the file exists.  If it does, it will serve that static page by reading the file contents via FileInputStream.  FileInputStream instance will stream chunks of bytes to the socket's OutputStream along with the Response Status Line and Header Fields.

If the file does not exist, it checks if you're attempting to visit the hello page.  If you were, it will display the parameters in a simple HTML table, separated in key and value columns.  It makes sure not to display parameters that only have keys listed.

Lastly, if neither the file exists nor you're visiting the hello page, it will send a 404 Not Found response.

## HTTY aka Heck To The Yeah aka Happy Trails To You

I found a [tweet](http://twitter.com/#!/coreyhaines/status/26947681246) yesterday morning from Corey Haines about [HTTY](http://htty.github.com/).  It's a "console application for interacting with HTTP servers.  It's something of a cross between curl and the Lynx browser."  Perfect!  I tried it out on my HTTP Server and sure enough, when I executed the get command on htty, it displayed the GET request on the server side.  This was a handy tool when testing out my HTTP server.  Of course, I also used all different kinds of browsers on Mac and Windows to see what the request protocol looks like.

## Poor man's load testing

Just to have fun and test out the SocketService, I kicked off the HTTP server and had a bunch of tabs opened on different parts of the local site and had them refresh every second.  I also held down refresh (Command + R) for a minute and regularly checked the Activity Monitor.  I think the highest I've seen it use threads was 20.  The CPU utilization was low.  I haven't tried looking for it on Google, but I'd like to see how it does on a network performance tool.  Anyone know of any?

## File serving

I ran a simple test to load a pdf and mp3 file and it worked out a hitch.  I've seen a consistent SocketException error on Chrome 7 where it tries to get the mp3 file three times.  Fortunately, the SocketException error does not effect the mp3 streaming and I was able to play the song on every try.

## Conclusion

This was a fun project.  I've learned so much about HTTP servers and how they work.  I've also learned a heck of a deal on multi-threading, although I can't say I'm an expert now.  This was a rewarding experience.  I hope the demo tomorrow will be smooth.
