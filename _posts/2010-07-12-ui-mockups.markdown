---
layout: post
title: ui mockups
date: 2010-07-12 19:30:00 -05:00
categories:
  -- software craftsmanship
  -- conference
  -- ux
---

*Tic Tac Toe - 4x4 board*

The 4x4 board implementation on Limelight was fairly straightforward.  I learned about the build command in Limelight to build props when a player is triggered.  This allows the user to select the board (3x3 or 4x4) and upon clicking the New Game button, it calls this method:

{% highlight ruby %}
  def build_squares
    @board.ranges.each do |r|
      scene.build do
        row do
          r.each do |s|
            square :id => "square_#{s}"
          end
        end
      end
    end
  end
{% endhighlight %}

CpuPlayer class required a bit more effort because of the regular expression pattern sets.  I created a basic version of the pattern sets for the 4x4 board.  It currently only knows when to win and block, but nothing in between (e.g., building itself a win).  The 8th Lighters around me suggested to create a true rules-based logic.  If I have more time, I'll look into this, but as of now, this should suffice.  Here's what it looks like now:

![TTT 4x4 board](/images/ttt_4x4_board.jpg)

*UI mockups using Balsamiq*

I created a couple of mockups on what I wanted the Tic Tac Toe UI to look like.  To be honest, it looks pretty much the same with an exception to the options (e.g., board size, players, start game button) which were moved to another scene.  Here are the mockups thus far.  I sent them to the customer so that he may review them and see if it's what he wanted.  I have a feeling he'll want something completely different.  I'll let you know.

Options

![TTT Options](/images/ttt_options.jpg)

Board

![TTT Board](/images/ttt_board.jpg)

*Ruby Midwest*

I'm attending the first [Ruby Midwest](http://rubymidwest.com/) conference in Kansas City later this week.  It's a two-day, single track conference, packed with some great [talks](http://rubymidwest.com/schedule.html).  I don't know about you, but I love single track conferences.  It's rewarding to be able to listen to every single talk.  I look forward to meeting more Rubyists and experience the Kansas City [BBQ](http://omgwtfbbq.heroku.com/).
