---
layout: post
title: future stories for tic tac toe
date: 2010-07-26 21:00:00 -05:00
categories:
  -- software craftsmanship
  -- mongodb
  -- ruby
  -- negamax
  -- stories
  -- apprenticeship
  -- retrospective
---

## New Stories for Iteration #5 and #6

Iteration #4 is not near its end, but Micah and I sat down today and created more stories for my Tic Tac Toe project.  The stories are going to be focusing on...drum roll please...throwing my Tic Tac Toe engine on a web app!  Cool!  I asked Micah a lot of questions regarding the stories.  For one, I'm not allowed to use any external gems, just standard Ruby libraries.  So goodbye, Rails, Sinatra, Rack, yadda yadda.  Fortunately, I have [erb](http://en.wikipedia.org/wiki/ERuby) on my side.  I'm not sure how valuable it is to have erb at this point, but I'm glad I have the option to use it.  I'll also be able to use [WEBrick](http://en.wikipedia.org/wiki/WEBrick), which is that HTTP web server people use to test their applications in a dev environment.  I'm going to have to do some reading about cookies and really understand how web applications used to work. 

## UI Story

![TTT Options Scene](/images/ttt_options_scene.jpg)

I continued working on the UI story.  It's coming along and so far I was able to get the options scene working.  I still need to add the custom listboxes for the options.  One problem I encountered in Limelight is that it couldn't find the mongo gem.  

{% highlight text %}
[master][~/local/git/tic_tac_toe_ruby] limelight open .
["/Users/skim/.rvm/gems/jruby-1.5.1/gems/limelight-0.5.5-java/lib", "/Users/skim/.rvm/gems/jruby-1.5.1/gems/jruby-openssl-0.7/bin", "/Users/skim/.rvm/gems/jruby-1.5.1/gems/jruby-openssl-0.7/lib", "/Users/skim/.rvm/rubies/jruby-1.5.1/lib/ruby/site_ruby/1.8", "/Users/skim/.rvm/rubies/jruby-1.5.1/lib/ruby/site_ruby/shared", "/Users/skim/.rvm/rubies/jruby-1.5.1/lib/ruby/1.8", ".", "/Users/skim/local/git/tic_tac_toe_ruby/lib", "/Users/skim/local/git/tic_tac_toe_ruby/lib"]
Exception in thread "AWT-EventQueue-0" /Users/skim/.rvm/rubies/jruby-1.5.1/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require': no such file to load -- mongo (LoadError)
	from /Users/skim/.rvm/rubies/jruby-1.5.1/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
	from /Users/skim/local/git/tic_tac_toe_ruby/lib/negamax_player.rb:9
	from /Users/skim/local/git/tic_tac_toe_ruby/lib/negamax_player.rb:31:in `require'
	from /Users/skim/.rvm/rubies/jruby-1.5.1/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
	from /Users/skim/local/git/tic_tac_toe_ruby/lib/player.rb:21:in `create'
	from /Users/skim/local/git/tic_tac_toe_ruby/default_scene/players/default_scene.rb:63:in `create_players'
	from /Users/skim/local/git/tic_tac_toe_ruby/default_scene/players/default_scene.rb:14:in `scene_opened'
	from /Users/skim/.rvm/gems/jruby-1.5.1/gems/limelight-0.5.5-java/lib/limelight/stage.rb:195:in `open'
	from /Users/skim/.rvm/gems/jruby-1.5.1/gems/limelight-0.5.5-java/lib/limelight/producer.rb:128:in `open_scene'
	from /Users/skim/local/git/tic_tac_toe_ruby/options_scene/players/options_scene.rb:23:in `play_new_game'
	from (eval):1:in `instance_eval'
	from /Users/skim/local/git/tic_tac_toe_ruby/options_scene/players/button.rb:12:in `mouse_clicked'
	from :1
	...internal jruby stack elided...
{% endhighlight %}

I had Micah come over to troubleshoot the problem and I found out that Limelight does not look at the system gems.  Instead you'll need to pull in the external gems you want to use into your project similar to how [Bundler](http://gembundler.com/) works.  By running this command, it will automagically pull in the gem:

{% highlight text %}
[master][~/local/git/tic_tac_toe_ruby] limelight freeze mongo
	creating directory:  ./__resources
	creating directory:  ./__resources/gems
	creating directory:  ./__resources/gems/gems
	creating directory:  ./__resources/gems/gems/mongo-1.0.5
	unpacking gem:       ./__resources/gems/gems/mongo-1.0.5
	creating directory:  ./__resources/gems/specifications
	creating file:       ./__resources/gems/gems/mongo-1.0.5/limelight_init.rb
{% endhighlight %}

You'll need to do this for dependencies as well:

{% highlight text %}
[master][~/local/git/tic_tac_toe_ruby] limelight freeze bson
	creating directory:  ./__resources/gems/gems/bson-1.0.4
	unpacking gem:       ./__resources/gems/gems/bson-1.0.4
	creating file:       ./__resources/gems/gems/bson-1.0.4/limelight_init.rb
{% endhighlight %}

I think in the future, Limelight will incorporate Bundler to handle external gems.

## Apprenticeship Retrospective

It's amazing how fast time flies.  I've been here for almost two months now, and it feels like I just started a couple of weeks ago.  Micah put two columns on the whiteboard, "Good" and "Improve On".  He and I both took turns writing things down on both columns.  Overall, I believe I'm on the right track.  To stress on what needs to improve, here is the list we wrote down:

* TDD
* story estimation
* continually read books
* focus/time box/pomodoro
* more pairing time
* wear all kinds of hats
* in-depth geekiness on current topics
* 0 point iteration
* meet commitments
* hobby project
* sustainable pace
* attend more user groups

As you may recall, one particular week, I came out of an iteration completing zero points.  How can anyone do that?  I need to practice estimating the stories better and give them points that allow me to work at a sustainable pace.  I'm going to have to figure out how to work on 10 points a week, work on a hobby project (which I can easily pick from my long list), read a book, attend more user groups, and play the ukukele with my feet.  Okay sans the last part.  Did I tell you I love this apprenticeship program?  No seriously, I'm learning so much, it's rewarding to learn from a group of passionate craftsmen. :)
