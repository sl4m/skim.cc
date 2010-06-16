---
layout: post
title: first day at the 8th light office
date: 2010-06-12 16:30:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
---

Yesterday was my first day at the 8th Light office as a software apprentice.  I was very excited to be there.  The entire day I focused on my Tic Tac Toe program continuing to further my extraction of methods into new classes.  I paired with another apprentice, [Li-Hsuan](http://twitter.com/Li_Hsuan) and we ping-ponged, writing tests and code for the HumanPlayer class.

Micah gave a great tip on how to mock stdin/stdout.  Ruby has global variables $stdin and $stdout which represent instances of the IO class.  Ruby also has constants (STDIN and STDOUT) which point to the same object reference as $stdin and $stdout.  I could have manipulated $stdin and $stdout to point to something else, but another way to do this is to pass in a stdin/stdout in my HumanPlayer class.

This is what HumanPlayer class looks like so far.

{% highlight ruby %} require 'player' class HumanPlayer < Player
  attr_reader :type, :input, :output

  def initialize(piece, input, output)
    super(piece)
    @type = 'human'
    @input = input
    @output = output
  end

  def make_move
    @output.print "\nEnter your move [0-8]: "
    @input.gets.to_i
  end
end
{% endhighlight %}

Here are the RSpec tests for HumanPlayer.

{% highlight ruby %}
# human_player_spec.rb
require File.expand_path(File.dirname(__FILE__)) + "/spec_helper"   
require 'human_player'
require 'stringio'

describe HumanPlayer do
  before(:each) do
    @input = StringIO.new
    @output = StringIO.new
    @human = HumanPlayer.new('O', @input, @output)
    @test_move = 4
  end

  it "should be able to return type of player" do
    @human.type.should == 'human'
  end

  it "should not make a nil move" do
    @human.make_move.should_not be_nil
  end

  it "should return a move from std in" do
    @input.string = @test_move.to_s
    @human.make_move.should == @test_move
  end

  it "should display message to player" do
    @human.output.should_receive(:print).with("\nEnter your move [0-8]: ")
    @human.make_move
  end
end
{% endhighlight %}
