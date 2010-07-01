---
layout: post
title: tic tac toe stories - part 2
date: 2010-06-30 18:00:00 -05:00
categories:
  -- software craftsmanship
  -- refactoring
---

I continued working on the Tic Tac Toe stories.  [Jason Catena](http://twitter.com/catenate) pointed out that I had placed all my ten stories in the Ready phase.  Good catch.  I took a snapshot of my AgileZen board before I changed it when Micah made aware of what I did.  The stories colored in red were moved to the Backlog.  [Jon Homan](http://twitter.com/jonhoman) sent me a [link](http://www.infoq.com/presentations/martin-jruby-limelight) to Micah's "Basking in the Limelight" presentation at last year's QCon.  I watched it last night and discovered bits of info I didn't know how to do in Limelight.  Things like testing players that require user interaction (e.g., mouse_clicked, key_pressed); you just have to call the method with a nil argument.

{% highlight ruby %}
prop.mouse_clicked(nil)
{% endhighlight %}

Also, the presentation explained how to package a production into a single, compressed file.  Bingo!  This is the answer to one of my stories, "Ability to double-click the application".  Of course, this is based on the assumption that the customer has the Limelight environment set up on his/her computer, but it should suffice.  It's actually very simple to package a production.  Simply execute this command:

{% highlight text %}
limelight pack production_name
{% endhighlight %}

It will create an \*.llp file which is really a \*.tar.gz behind the scenes, but when you double-click the file, Limelight associates with it and will open the application.  I uploaded my first \*.llp on GitHub and it's available in the [Downloads](http://github.com/sl4m/tic_tac_toe_ruby/downloads) section.

I spiked several stories and seemed to have a better idea of what I need to do for those stories.  One in particular, I code spiked to create randomness in the way it moves in the MinMaxPlayer class.  I don't think my minmax algorithm is quite working as I'd thought.  Micah was able to set it up where it would not take the best move to win quickly.  It's able to defend and sometimes win, but not look for quick wins.  Here's an example:

![MinMax Fail](/images/min_max_fail.jpg)

I'll need to work on this in the next iteration.  I also spiked the story where it described the MinMax player as being slow.  Truthfully, it is slow, but only the first minmax algorithm call.  Any call after that is fairly quick.  I'll still need to look into the performance issue though if I want to implement the 4x4 board story.  One of the 8th Lighters, [Craig](http://twitter.com/demmer12), told me about [ruby-prof](http://ruby-prof.rubyforge.org/), a ruby profiler that supports recursive calls, so I took some time to read about it.  Apparently, [this guy](http://twitter.com/danlucraft) created a [JRuby version](http://danlucraft.com/blog/2010/03/jruby-prof/) of it, so I used it instead.  I added the profiler code in min_max_player.rb and ran it.

{% highlight ruby %}
if $0 == __FILE__
  require 'rubygems'
  require 'jruby-prof'
  require 'std_ui'

  result = JRubyProf.profile do
    min_max_player = MinMaxPlayer.new('O')
    min_max_player.board = Board.new
    min_max_player.ui = StdUI.new
    puts min_max_player.make_move
  end

  JRubyProf.print_flat_text(result, "flat.txt")
  JRubyProf.print_graph_text(result, "graph.txt")
  JRubyProf.print_graph_html(result, "graph.html")
  JRubyProf.print_call_tree(result, "call_tree.txt")
  JRubyProf.print_tree_html(result, "call_tree.html")
end
{% endhighlight %}

Sadly, it took a very long time since profiler takes a little bit more time to execute the code.  Here are the results in five different formats.  I have not taken a look at it carefully, but hopefully it'll give me some answers as to why it's slow.

[flat.txt](/files/flat.txt)
[graph.txt](/files/graph.txt)
[graph.html](/files/graph.html)
[call_tree.txt](/files/call_tree.txt)
[call_tree.html](/files/call_tree.html)

You can read more about what each of these files mean [here](http://danlucraft.com/blog/2010/03/jruby-prof/).

Lastly, I'm working on a story that is all about the aesthetics of the program.  It's described as "Design and build a stunning LL UI with unprecedented usability, animated transitions, and tasteful eye candy."  The customer gave me a list of examples he wanted and I foolish enough to ask for examples.  Now I basically have to implement every example he asked for.  I have a few ideas to make the UI more eye candy and I'll need to read up on how use the animation feature in Limelight.  More on this tomorrow.
