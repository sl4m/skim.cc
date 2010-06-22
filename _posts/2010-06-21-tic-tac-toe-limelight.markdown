---
layout: post
title: tic tac toe on limelight
date: 2010-06-21 22:30:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- limelight
---

*Note:* I accidentally deleted a draft of this post, so this might not be as good as the first.

My Tic Tac Toe project continues this week, developing a UI (instead of stdin/stdout) to display the board and players.  Micah wants me to use 8th Light's very own [Limelight](http://limelight.8thlight.com/).  It's an open source, platform independent, rich client GUI framework.  It uses unique theatre metaphors (e.g., productions, scenes, props, players) to entertain developers; they build productions (not applications) to "razzle-dazzle" their audience.  To stick with the metaphor, the word [Limelight](http://en.wikipedia.org/wiki/Limelight) itself is by definition a type of stage lighting once used in theatres and music halls.  All productions are written using Ruby and specifically uses the JRuby interpreter.

* Getting Started *

I installed JRuby using RVM and proceeded to install the limelight gem.  To create a new Limelight production you do the following (note: my production name is limelight_test) :

{% highlight text %}
[~/local/limelight] limelight create production limelight_test
	creating directory:  ./limelight_test
	creating file:       ./limelight_test/production.rb
	creating file:       ./limelight_test/stages.rb
	creating file:       ./limelight_test/styles.rb
	creating directory:  ./limelight_test/spec
	creating file:       ./limelight_test/spec/spec_helper.rb
	creating directory:  ./limelight_test/default_scene
	creating file:       ./limelight_test/default_scene/props.rb
	creating file:       ./limelight_test/default_scene/styles.rb
	creating directory:  ./limelight_test/default_scene/players
	creating directory:  ./limelight_test/spec/default_scene
	creating file:       ./limelight_test/spec/default_scene/default_scene_spec.rb
{% endhighlight %}

You may immediately notice how similar it looks to a newly generated Rails app.  The file structure, however, is different.  Using the theatre metaphors, every scene contains at least one prop.
