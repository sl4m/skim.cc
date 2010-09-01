---
layout: post
title: rails and tic tac toe webrick
date: 2010-08-31 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
  -- tic tac toe
  -- webrick
---

Matt and I managed to resolve the issue I discovered last night.  The solution was easier than I thought.  There's yet more Rails conventions that I'm don't know about and [Active Record Observer](http://api.rubyonrails.org/classes/ActiveRecord/Observer.html) is one of them.  We found the methods that sent emails to users upon registration and activation and we added a conditional logic to prevent emails from being sent.  Paul wanted a couple of other minor visual fixes, so we found the erb file responsible for the view and fixed them.  I pushed the changes to the repo and pulled it down from the staging server to execute a practice run and it ran without a hitch.  Last I heard it's being deployed to production.  I'm pretty excited to see a feature we implemented go live.  This is probably first major feature I've implemented.  I look forward to working on more features in the future.

During the day I spent some time reading some Ruby blog posts and picking up Well Grounded Rubyist again.  Blog posts by John Nunemaker showed examples about [building an object mapper](http://railstips.org/blog/archives/2010/08/29/building-an-object-mapper-override-able-accessors/) and his previous post on how [Ruby's method lookups work](http://railstips.org/blog/archives/2009/08/20/lookin-on-up-to-the-east-side/).  It's interesting when including a module in a class and overriding the module's method, you're able to call the module's method by calling *super*.  Building an object mapper is slightly more complicated and really neat at the same time.  I can't think of a use case for it other than John's mention of MongoMapper.  Like Paolo Perrota said in his talk though, I think it's good to understand how to do the cool tricks.

## Tic Tac Toe WEBrick

I'm going to work on a story for my Tic Tac Toe project to allow multiple players each play their own game on WEBrick.  This will require exchanging cookie information and possibly changing the way the servlet works.  By default, WEBrick creates new instances of every servlet mounted on the server.  This unfortunately doesn't work in my situation because I need to keep the same game instance.  I'm going to see if I can somehow use cookies while preserving the code that I have to keep the same instance.

{% highlight ruby %}
  def self.get_instance config, *options
    @@instance_creation_mutex.synchronize do
      @@instance = @@instance || self.new(config, *options)
    end
  end
{% endhighlight %}
