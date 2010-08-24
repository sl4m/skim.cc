---
layout: post
title: storing 4x4 on mongodb - part 2
date: 2010-07-20 21:00:00 -05:00
categories:
  -- software craftsmanship
  -- mongodb
  -- nosql
  -- ruby
---

> "If you count something interesting, you will learn something interesting" \- Apprenticeship Patterns, [Create Feedback Loops](http://apprenticeship-patterns.labs.oreilly.com/ch05.html#create_feedback_loops)

## Writing to MongoDB Fail

Note to self: If you're going to generate 16! board states for a 4x4, make sure the associated values are correct after the first thousand generated.

I failed to analyze the generated data stored in my local MongoDB and found out after writing 122 million documents that the best moves were stored as NULL.  It was because of an unfamiliar territory called block scope.  In JavaScript, there is no block scope which I'm used to.  Functions are pretty much the only scope.  However, in Ruby, block scope exists. So what I failed to do in the method is create an initial value outside the block.  D'oh.

I was also displaying each board state in a puts method and used JRuby to execute the method.  Since JRuby [does not support C\-extensions](http://blog.headius.com/2010/07/what-jruby-c-extension-support-means-to.html) at this time, it means it does not support a gem called [bson\_ext](http://rubygems.org/gems/bson_ext) which accelerates the Ruby BSON serialization for MongoDB.  [Kyle Banker](http://github.com/banker) is working on a [Java version of bson\_ext](http://blog.headius.com/2010/07/what-jruby-c-extension-support-means-to.html?showComment=1279659170383#c6373087544021608188), but I'm not sure when it'll be ready.  Reading yesterday's [Ruby shootout](http://programmingzen.com/2010/07/19/the-great-ruby-shootout-july-2010/) revealed Ruby 1.9.2 to be among the top performers, so I installed 1.9.2\-preview3 using rvm and installed bson\_ext gem.  I'm now executing the method again.  One thing to note, I fixed the block scope issue above by setting the best\_move variable to \-1.  However, I noticed some board states still had a best\_move == \-1 when it should have changed to a value 0\-15.  After some time investigating, I found out the reason why it was \-1 was because the board was in a state where it was *not* Negamax's turn.  Meaning the recursive call was for other player's move.  Since I only care about board states when it's Negamax's turn to move, I don't need to store these board states to MongoDB.  This should shave off time and storage space. 

## Limelight UI

![TTT Nuclei](/images/ttt_nuclei.jpg)

To experiment placing images on my Limelight UI default scene, I quickly created several background images to replace my [ugly gradient background](http://skim.cc/2010/07/12/ui-mockups/) for my Tic Tac Toe program.  It's pretty easy to set the background image.  In the styles.rb file, I just added this snippet:

{% highlight text %}
default_scene {
  background_image "images/background_nuclei.jpg"
}
{% endhighlight %}

I'm going to experiment with adding the board lines and pieces to the UI and attempt to create new stages for the options and "try again" dialog.
