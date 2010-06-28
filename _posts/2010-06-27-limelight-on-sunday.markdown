---
layout: post
title: limelight on sunday
date: 2010-06-27 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- limelight
---

I finished the Limelight UI implementation today.  I learned a lot simply by looking at Micah's hangman example.  The Limelight documentation was not clear in some places, so most of my questions were answered in the code.  I think [using the source code](http://apprenticeship-patterns.labs.oreilly.com/ch05.html#use_the_source) is a great way to learn, especially a framework you're not familiar with.

![Limelight Tic Tac Toe Final](/images/limelight_tic_tac_toe_final.png)

I installed the EAP (early access program) version of [RubyMine](http://www.jetbrains.com/ruby/index.html) on my Windows box, so I can have two IDEs opened on two separate screens.  I tried having two IDE instances on two different spaces on my MBP, but it kept wanting to group together to the same space.  Big Bummer.  Having two separate IDEs though helped tremendously.  I don't know how many times I looked at the same file and same piece of code, over and over, but until I understood it, I kept looking.  One area I still had trouble was remembering how to access props in a scene ([Limelight theatre metaphor](http://limelightwiki.8thlight.com/wiki/A_Cook%27s_Tour_of_Limelight#Theater_Metaphor)).  Depending on which file you're in, you can access a prop several different ways:

{% highlight ruby %}

# in a spec
scene.prop

# in a scene
prop

# in a prop's player
self
scene.other_prop
{% endhighlight %}

Another area which I had trouble was TDD.  Without fully grasping the knowledge of the Limelight framework, I did a lot of code spiking.  I ended up writing tests for the implemented features, but I did not scrap the code and start with TDD.  I guess I was too afraid to lose precious information that I just discovered and might forget during TDD.  Also, the project is due tomorrow, so I didn't want to take the chance.  This is something, however, I need to improve.

The final bit was using a Thread instance to run my game logic.  In my previous post, I talked about how I created GUI utilities using KiXtart/KiXforms.  Unfortunately, KiXtart has no multi-thread support, so I had to overcome problems where multiple events were being fired at the same time.  I have not worked with a language that supports multiple threads, but it overcame a problem I thought about in my head when thinking about the event loop.  If Limelight UI has control of the event loop, and the game logic has its own loop, how will they work together?  By creating a new Thread instance for the game logic, I was able to have them both communicate with the use of values passed around in instance variables.

I ran a quick test to make sure the legacy stdin/stdout works, and it does.  I'm noticing a bit of un-DRY-ness with the two UIs, so I will need to do a bit of refactoring.  Overall, I'm pretty happy with it.
