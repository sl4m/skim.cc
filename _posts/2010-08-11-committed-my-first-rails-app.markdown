---
layout: post
title: committed my first rails app
date: 2010-08-11 11:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
  -- chicago
---

Today was a pretty fun, exciting day.  I took the train down in the morning to go to the Chicago office where I worked on my first Rails app!  The idea was to come down for the day to assist Paul on a simple task - replace JavaScript rendering banners with a flash-based banner per client's request.  Paul gave me write permission to commit to the GitHub repo and I went ahead and cloned the repository to discover what this Rails app was made of.

After a bit of trouble setting up the required gems (this project could use [Bundler](http://gembundler.com/)) to run the tests, I needed to figure out how to embed a flash file.  Now I could have done a bit more research to find what's the best way to embed the flash file, but I chose something that immediately came out of a Google search.  It's a Rails plugin called [swf\_fu](http://github.com/marcandre/swf_fu) which makes it super easy to embed flash files using its own tag method:

{% highlight erb %}
<%= swf_tag "flash_file" %>
{% endhighlight %}

After including the swfobject.js file, it does its magic.  I made sure the tests continued to pass and made sure the flash file visually rendered correctly.  I proceeded to remove references of the JavaScript banners, but had a bit of trouble with the database.  Paul stepped in and helped me solve the problem.  You just don't mess with the schema.rb file.  D'oh.

I made the tests pass again after removing the old banner references and pushed my changes to GitHub.  That felt good.  It might've been a small task, but I enjoyed contributing.  Paul asked me to do another small task that sounds a bit more challenging.  I'm basically creating a new Rails app that can send a post form.  I'm constantly reading the [Rails Guides](http://guides.rubyonrails.org) and googling around for some ideas.  I may end up falling back on a gem (no pun intended).

## WEBrick Tic Tac Toe

Micah and I were supposed to have our end of iteration meeting today, but missed each other via Skype.  He's at the Agile 2010 conference, so it was a bit tough coordinating the time.  We will try tomorrow.  Basically, an update from yesterday's news on the WEBrick project, I was able to fake GET requests by polling a refresh every two seconds using the meta tag.  It still produces weird board glitches and the usability is kind of hokey, but it does work.  Hopefully, Micah will give advice on how to resolve the situation.  I heard he's built many web servers, most of which eat WEBrick alive.
