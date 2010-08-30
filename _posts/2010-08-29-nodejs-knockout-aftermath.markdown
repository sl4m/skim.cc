---
layout: post
title: node.js knockout aftermath
date: 2010-08-29 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- nodejs
  -- websocket
  -- knockout
---

[Node.js Knockout](http://nodeknockout.com/) was this weekend and it was a great learning experience.  I highly recommend everyone to experience a high adrenaline, 48 hour coding spree at least once to really understand team dynamics, importance of communication, the advantages of pair programming, and dealing with head-on challenges.

I think everyone in the team felt the same way in the beginning of the knockout, whether or not we'll produce something out of the 48 hours.  Unfortunately, we were a little unprepared.  Personally, I felt very unprepared and should have had read about HTML5's features like websocket, canvas, and learn how to use third party libraries like Faye, PusherApp, jQuery, etc.  Unfortunately, like all of my past excuses, time was limited and I could not get to the reading.  What was great though was that we didn't give up and we trekked on, learning new technologies on-the-fly, communicating with each other to come up with stories, with what events the server needs to fire, what events the client needs to fire, what bugs do we see, and so on.  Although, it was a bit rough in the first six hours, we used the next twenty-seven to build something out of thin air.

## What the heck did you make?

We created a multiplayer tank game using new technologies: HTML5 websocket, canvas, and node.js. This is the Node.js Knockout after all.  Before I take you down the yellow brick road, here is the link to our game: [Nōdo Tanku](http://ko-8thlight.no.de/).  It requires any of the following supported browsers:

* Chrome 5 or greater
* Safari 5 or greater
* Firefox 4 Beta 1 or greater

It basically relies on a browser that supports websocket draft 75 or 76 because that is what Faye client/server relies on.  Fortunately, Faye supports both.

Although, our game comes with a good number of bugs, I think we all agreed as a team that we pulled the almost impossible.  We're all very happy with what we deployed to Joyent.  I think the sound effects added another element to the overall game experience.  The hand drawn tanks, some jQuery jazz, and almost hard-to-read TypeKit font made the game super fun.

## What I need to improve

Fortunately, we all watched PeepCode's Node.js screencast.  This was our foundation of how we structured both the server side and client side JavaScript.  The thing I regret the most not doing is not TDD'ing the client side JavaScript code.  Craig and I were pretty much the client side team, while Jim and Justin were the server side team.  I'm happy they used Hudson CI and Jasmine Node to test their server side JavaScript, but because I was not familiar with client side testing frameworks or libraries, I did not test drive our client side libraries.  This introduced some bugs that were created when adding new features.  I'm pretty sure there were several occasions where I implemented a new feature, and later another team member reported a problem with existing functionality.  I need to test first!

Other things I need to improve on is my CSS and overall understanding of the HTML5 features.  I think probably half of the time, I was doing a lot of reading to understand how to implement things here and there.  That time could have been spent creating tests first, implementing more features, fixing bugs.

## Vote for us!

This post cannot be said without saying, you should vote for us!  Well...vote for us if you like our game.  I had so much fun working with the other 8th Lighters.  I think we all had a lot of fun and enjoyed playing our own game.  We hope you do too.

[Vote Here!](http://nodeknockout.com/teams/8thlight)
