---
layout: post
title: rails and node.js - part 5
date: 2010-08-26 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
  -- patterns
  -- nodejs
  -- websocket
---

We finished the API features for the Rails project and did a bit of refactoring.  As the feature set grew, it made more sense to rename refactor the namespace, methods, etc.  We also used extract method refactoring to move methods into a new module where it made more sense.  The final piece of this is to write a script that will use the API methods to retrieve customer information and update the database with that information.  We tried creating a script that was placed in the script folder, but unfortunately could not require the API module we created.  We may look into creating a Rake task and have Rake load the Rails environment.  I'll have to look into how Rake tasks work.  This will go live next Monday, so I'm a bit excited and nervous.  I look forward to putting on the finishing touch tomorrow and run a quick demo with Paul.

I forgot to mention yesterday Matt and I worked on some XML data and used Ruby's standard library, rexml, to do the job.  It's actually fairly easy library to use.  The entire xml is stored in an *elements* hash and by providing it the XPath, it will return the element(s).

## Node.js

Unfortunately, I didn't make head way in the Node.js, HTML5 reading as I hoped.  I guess I'm a little burned out from the week, but I look forward to working on our Node.js Knockout project this weekend.  Apologies for the short blog post, but I will have lots to talk about after this weekend.
