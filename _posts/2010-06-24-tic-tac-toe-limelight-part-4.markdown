---
layout: post
title: tic tac toe on limelight - part 4
date: 2010-06-24 23:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- limelight
---

Today was a continuation of this week's Limelight project; understanding how to leverage the Limelight library to create a GUI for my Tic Tac Toe program.  Here's the work-in-progress look of it:

![Limelight Tic Tac Toe](/images/limelight_tic_tac_toe.png)

I had trouble getting those comboboxes appear in the "scene".  My fellow apprentice mate, Li-Hsuan, handed down good advice and told me to create a new production and just add the comboboxes.  Lo and behold, it worked.  I've been taking notes as I read along and work out example code.  This is a short version of it:

Hierarchical view of a Limelight production:

{% highlight text %}
production (process)
|
-- stages (like a window)
   |
   -- scenes (master of props)
      |
      -- props (controls)
         |
         -- styles (visual look of controls)
         |
         -- players (events)
{% endhighlight %}

Limelight DSLs

* ProductionBuilder
* StageBuilder
* PropBuilder
* StylesBuilder

Built-in Players

* button
* check_box
* combo_box
* radio_button
* text_area
* text_box

I plan to stick with a production that contains one stage, one scene with the props you see in the above picture.  I want to make it as simple as possible and integrate it with the Tic Tac Toe code I've already developed.  I already know there will be parts in the code that I'll need to change to accomodate the new UI.  At this point you probably already know that I will not meet my deadline.  I ended up pushing it to next Monday and Micah was very cool with it.  I feel like I haven't progressed as much as I'd like, but hopefully tomorrow and the weekend, I'll nail the UI code.


