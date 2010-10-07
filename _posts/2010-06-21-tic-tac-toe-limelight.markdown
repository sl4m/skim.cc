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

The project you thought would end, continues this week with a new challenge; I am to a build a UI interface for my Tic Tac Toe program (instead of stdin/stdout).  Micah wants me to use 8th Light's very own [Limelight](http://limelight.8thlight.com/).  It's an open source, platform independent, rich client GUI framework.  It uses unique theatre metaphors (e.g., productions, scenes, props, players), similar to the [MVC design pattern](http://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller), for the sake of entertaining developers - build productions, not applications to "razzle-dazzle" the audience.  [Limelight](http://en.wikipedia.org/wiki/Limelight) itself means a type of stage lighting once used in theatres and music halls.  Also the name contains ["light"](http://limelightwiki.8thlight.com/wiki/A_Cook%27s_Tour_of_Limelight#Theater_Metaphor).  Pretty clever.  All productions are written using Ruby and are interpreted using [JRuby](http://jruby.org/).

## Getting Started

I installed JRuby using [RVM](http://rvm.beginrescueend.com/) and proceeded to install the limelight gem.  I then created my very first Limelight production using the following command (note: my production name is limelight_test) :

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

You may immediately notice how similar it looks to a newly generated Rails app.  The file structure, however, is different, taking on the theatre metaphor.  Here's a brief description:

{% highlight text %}
+ default_scene - Each scene is in its own folder.
  + players - Contains Players (controllers) for the Scene.
  + props.rb - Specifies the Prop structure for the Scene.
  + styles.rb - Specifies the Styles for the Scene.
+ spec - Your tests go here (RSpec, Cucumber)
+ production.rb - For configuring the Production.
+ stages.rb - Defines and configures the Stages in the Production.
+ styles.rb - Production Styles go here, shared across all scenes.
{% endhighlight %}

Every production contains at least one scene that contains props.rb and styles.rb.  One piece of information the description above does not say is that the players can also be placed on the production level.  Partials are also supported for Props (views) for some DRY action.

I went through a brief tutorial in the Limelight Docs and found myself building a quick calculator.  However, out of that process, I began spiking code to get a better understanding of productions, scenes, props, styles, players, and to get a visual look of what I wanted for the Tic Tac Toe board.  I've done similar UI style coding in the past using a deprecated UI library for a deprecated Windows-only interpreter.  Anyone heard of [KiXtart](http://www.kixtart.org/) and [KiXforms](http://www.kixforms.org/)?  Yeah I bet not.  While the KiXtart language itself was not elegant or expressive like Ruby and KiXforms was not an MVC framework, it did give experience on how to define "props", "styles", and "players" via code.

Tomorrow, and until Friday of this week, I plan to work on the UI portion of the program and somehow wire it all together.  Micah wants me to practice my project estimations.  I told him I would have it completed by Friday after a quick evaluation of what kind of work is required.  I just hope I can meet the deadline.


