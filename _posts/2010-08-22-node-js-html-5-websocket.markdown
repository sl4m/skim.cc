---
layout: post
title: node.js, html5, websocket 
date: 2010-08-22 22:00:00 -05:00
categories:
  -- software craftsmanship
  -- javascript
  -- nodejs
  -- html5
  -- websocket
---

I spent some time this weekend learning about HTML5, websocket, [Faye](http://faye.jcoglan.com/), [PusherApp](http://pusherapp.com/), and more in preparation for the [Node.js Knockout](http://nodeknockout.com/) next weekend.  There's a lot of content to cover.  [HTML5](http://en.wikipedia.org/wiki/HTML5) is the new standard of HTML superseding HTML 4.01, XHTML 1.0, and XHTML 1.1.  [Websocket](http://en.wikipedia.org/wiki/WebSockets) is a feature in HTML5 that allows for bi-directional, full-duplex communication channels.  I'm sure you know about all of this already, so I'll link some references I discovered over the weekend:

* [Dive into HTML5](http://diveintohtml5.org/) by Mark Pilgrim
* Firefox 4 (pre-beta 1), Chrome 5, and Safari 5 use websocket [draft 75](http://tools.ietf.org/html/draft-hixie-thewebsocketprotocol-75)
* [Firefox 4 (beta 1+)](http://hacks.mozilla.org/2010/07/firefox-4-beta-1-is-here-whats-in-it-for-web-developers/) and [Chrome 6](http://blog.chromium.org/2010/06/websocket-protocol-updated.html) use websocket [draft 76](http://tools.ietf.org/html/draft-hixie-thewebsocketprotocol-76)
* [PusherApp](http://pusherapp.com/) - client/server messaging system
* [Faye](http://faye.jcoglan.com/) -  client/server messaging system (supports websocket draft 75/76)
* Node.js third party library compatibility [list](http://github.com/ry/node/wiki/Library-compatibility)
* Node.js Knockout blog [post series](http://nodeknockout.posterous.com/) on how to use Node.js
* Node.js [prizes](nodeknockout) (are you motivated?)

There's an interesting relationship between implementation and specification and how one can influence the other.  When I think about Google, Mozilla, Apple, and even Microsoft implement the latest draft into their "edge" version browsers, I can see how their implementation styles can drive the specification of HTML5 in their favor when it's finalized.  [Mark Pilgrim](http://diveintomark.org/about), author of [HTML5 Diving Up and Running](http://www.amazon.com/HTML5-Up-Running-Mark-Pilgrim/dp/0596806027?ie=UTF8&tag=diveintomark-20&creativeASIN=0596806027), is right about the fact that "the ones that win are the ones that ship."  It's basically [how the img tag became standard](http://diveintohtml5.org/past.html).

Throughout this week, I plan to learn more on HTML5 and websocket.
