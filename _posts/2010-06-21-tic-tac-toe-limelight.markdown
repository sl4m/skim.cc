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

The project you thought would end, continues this week with a new challenge.  I am to a build a UI interface for my Tic Tac Toe program to display the board and players (instead of stdin/stdout).  Micah wants me to use 8th Light's very own [Limelight](http://limelight.8thlight.com/).  It's an open source, platform independent, rich client GUI framework.  It uses unique theatre metaphors (e.g., productions, scenes, props, players), similar to the [MVC design pattern](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller), for the sake of entertaining developers - build productions (not applications) to "razzle-dazzle" the audience.  [Limelight](http://en.wikipedia.org/wiki/Limelight) itself means a type of stage lighting once used in theatres and music halls.  Also the name contains ["light"](http://limelightwiki.8thlight.com/wiki/A_Cook%27s_Tour_of_Limelight#Theater_Metaphor).  Pretty clever.  All productions are written using Ruby and are interpreted using [JRuby](http://jruby.org/).

* Getting Started *

I installed JRuby using [RVM](http://rvm.beginrescueend.com/) and proceeded to install the limelight gem.  To create a new Limelight production you execute the following command (note: my production name is limelight_test) :

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

You may immediately notice how similar it looks to a newly generated Rails app.  The file structure, however, is different.  Here's a brief description:

{% highlight text %}
+ default_scene - Each scene is in its own folder.
  + players - Contains Players (controllers) for the Scene.
  + props.rb - Specifies the Prop structure for the Scene.
  + styles.rb - Specifies the Styles for the Scene.
+ spec - Your tests go here (RSpec, Cucumber)
+ production.rb - For configuring the Production.
+ stages.rb - Defines and configures the Stages in the Production.
+ styles.rb - Production Styles go here, shared across all scenes.

Using the theatre metaphors, every production contains at least one scene that contains props.rb and styles.rb.  One piece of information the description above does not say is that the players can also be placed in the production level.  Partials are also supported for Props (views) for some DRY action.


