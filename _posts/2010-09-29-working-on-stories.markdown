---
layout: post
title: working on stories
date: 2010-09-29 18:00:00 -05:00
categories:
  -- software craftsmanship
  -- yak shaving
  -- java
  -- stories
  -- tic tac toe
---

This morning, I started off with a quick fix to my Tic Tac Toe project.  When I updated JRuby to 1.5.3, I wanted to run my Limelight Tic Tac Toe to make sure it was working.  To my surprise, the Negamax player kept erring out.  Upon looking at the code I found out I got away with using *Object\#returning*, a Rails method, inside my NegamaxPlayer class.  I'm not sure how that was possible.  When I ran the specs, all Negamax player tests were failing.  I then discovered *Object\#returning* is a Rails method via Google search.  Fortunately, this was an easy fix.  Just get rid of *Object\#returning*.

{% highlight ruby %}
def indexes_of_max(array)
  max = array.max
  indexes = []
  array.each_with_index do |e, i|
    indexes << i if e == max
  end
  indexes
end
{% endhighlight %}

Specs are happy and the change is now pushed to the GitHub repo.

## Pull Request accepted for Statemachine gem

I'm happy to say this is probably my first official open source contribution.  It wasn't a significant fix or improvement to the library, but fixed a very minor issue when generating statemachine code in Java.  Check it [out](http://github.com/slagyr/statemachine/commit/114e0d47a7f30e0324f1649ed95d3430001a925b).

## Comment support in Limelight Styles Parser

I thought about adding a superstate, but decided to handle it on my own through custom code.  Comments are different than the other characters because once you enter in a comment, every character is part of the comment until new line.  So my transition list is a bit longer.  I trap comments for all states into a comment\_mode state where I don't act on any character except new line.

{% highlight ruby %}
def generate_parser_sm
  sm = Statemachine.build do
    trans :nothing, :comment, :comment_mode, :enable_comment_flag
    trans :nothing, :whitespace, :nothing
    trans :nothing, :new_line, :nothing
    trans :nothing, :open_curly_brace, :nothing, :error
    trans :nothing, :close_curly_brace, :nothing, :error
    trans :nothing, :alphanumeric, :name, :add_to_name
    trans :name, :comment, :comment_mode, :enable_comment_flag
    trans :name, :alphanumeric, :name, :add_to_name
    trans :name, :whitespace, :finding_curly
    trans :name, :new_line, :finding_curly
    trans :name, :open_curly_brace, :finding_attributes, :create_style
    trans :finding_curly, :comment, :comment_mode, :enable_comment_flag
    trans :finding_curly, :whitespace, :finding_curly
    trans :finding_curly, :new_line, :finding_curly
    trans :finding_curly, :open_curly_brace, :finding_attributes, :create_style
    trans :finding_attributes, :comment, :comment_mode, :enable_comment_flag
    trans :finding_attributes, :whitespace, :finding_attributes
    trans :finding_attributes, :new_line, :finding_attributes
    trans :finding_attributes, :close_curly_brace, :nothing
    trans :finding_attributes, :alphanumeric, :attr_name, :add_to_attr_name
    trans :attr_name, :comment, :comment_mode, :enable_comment_flag
    trans :attr_name, :alphanumeric, :attr_name, :add_to_attr_name
    trans :attr_name, :whitespace, :finding_attr_value
    trans :finding_attr_value, :comment, :comment_mode, :enable_comment_flag
    trans :finding_attr_value, :whitespace, :finding_attr_value
    trans :finding_attr_value, :alphanumeric, :attr_value, :add_to_attr_value
    trans :attr_value, :comment, :comment_mode, :enable_comment_flag
    trans :attr_value, :alphanumeric, :attr_value, :add_to_attr_value
    trans :attr_value, :close_curly_brace, :nothing
    trans :attr_value, :whitespace, :attr_value
    trans :attr_value, :new_line, :finding_attributes, :add_attribute
    trans :comment_mode, :new_line, :comment_mode, :disable_comment_flag
    trans :comment_mode, :alphanumeric, :comment_mode
    trans :comment_mode, :whitespace, :comment_mode
    trans :comment_mode, :open_curly_brace, :comment_mode
    trans :comment_mode, :close_curly_brace, :comment_mode
    trans :comment_mode, :comment, :comment_mode
    startstate :nothing
  end
  sm.to_java(:output => SRC_DIR, :name => "LLParser", :package => "limelight.parser")
end
{% endhighlight %}

Two things are involved.  In the context class, I created a privatized variable that stores the comment flag.  This flag determines whether or not the parser is in comment\_mode or not.  Right before it sets the flag to true when it enters the comment\_mode, I set the state to a privatized variable in the main file (LLStyles.java).  This is the state right before it enters comment\_mode state, so I can go back to the state when I'm out of comment\_mode state.

I'm sure there's a better solution, probably by using superstate.  But it works and I'm pretty happy about it.  It handles this [styles.rb](http://github.com/sl4m/limelight_styles_converter/blob/master/example/commented_styles.rb) file just fine.

## Tic Tac Toe Java

I'm now working on the Java implementation of Tic Tac Toe.  Fortunately, I don't have to implement 4x4, therefore I do not need to support MongoDB.  I also do not need to support additional computer players other than the Negamax player.  This is the list of classes I'll need to implement:

* Board
* Game
* HashCache
* HumanPlayer
* NegamaxPlayer
* NilCache
* Player
* UI

