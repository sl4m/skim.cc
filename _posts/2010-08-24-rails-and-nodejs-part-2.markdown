---
layout: post
title: rails and node.js - part two
date: 2010-08-24 23:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
  -- patterns
  -- nodejs
  -- websocket
---

Matt and I finished the Rails feature that we started yesterday.  What I thought would be a difficult task to log a user without a password, ended up being fairly simple.  The authentication call was the gatekeeper and determined if the user was allowed to log in.  If the authentication method was never called, you can just log the user in.  Now of course, we're not going to do that.  We created a simple class that returns a user if the user is coming from the third party site with valid params.  Then the log in method takes the user object and logs her in.

Our next feature involves working with several APIs that depend on each other.  We basically need to call these APIs in a background process to synchronize a table in our database with the third-party database.  I've not worked with background processes (e.g., cron jobs) before, but this will be an exciting challenge.  I asked Colin about it and he suggested we look into [Resque](http://github.com/resque).  I read [defunkt's](http://twitter.com/defunkt) [reasons](http://github.com/blog/542-introducing-resque) behind creating Resque after experiencing with many other background job systems for GitHub.  I like the fact that Resque has a manager aka monit/god who can watch the workers and make sure they're doing the job in a timely manner.  It's also heavily inspired by [DelayedJob](http://github.com/collectiveidea/delayed_job) which I was also looking into prior to Colin's suggestion.  defunkt "recommends DelayedJob to anyone whose site is not 50% background work."  I'll look into both and see which will be easier to implement.  Fortunately, both of them are still in active development.

## Reading

I spent some time reading a bit on the Rails conventions.  Database table names are pluralized, models are singular, file names are lowercased and underscored, while the classes are camelcased (e.g., IAmAClass).  Now I know Rails, behind the scenes, converts the names automatically to conventionally call things naturally.  Another interesting bit was how Rails automatically loads everything up.  This is why you rarely see require commands in the code.  Even libraries in the lib folder automatically load up.  We ended up storing our api library in a sub-folder of lib and since the classes were under a common module, it was automatically loaded up in the environment.  Conventions rule.

## Node.js Knockout Preparation

Craig just gave a heads up that Heroku does not support websockets.  Drats.  I believe PusherApp should still work since it works via REST, so we may end up using that.  I actually do not see another option at this point unless we build our REST + websocket server system (a replica of PusherApp).  I digress.  PeepCode Screencasts just came out with a [Node.js screencast](http://peepcode.com/products/nodejs-i) that I may end up buying and watching before the knockout.  While I enjoyed reading Dave Hoover's GroupDASHpon code, I guess it won't hurt to see how Geoffrey Grosenbach implements Node.js.  

I've noticed a lot of Rubyists have similar "coding styles" a lot more than any other languages I've used.  JavaScript is no exception.  Actually, I think a lot of JavaScript developers/hackers just write code that either follows the convention of the js framework/library or just makes things up, like add a bit of [Ruby flavor](http://ozmm.org/posts/javascript_style.html).  I know Douglas Crockford doesn't like the idea of using $ and \_ by itself to represent a namespace.
