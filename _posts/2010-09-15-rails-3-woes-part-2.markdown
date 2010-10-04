---
layout: post
title: rails 3 woes - part 2
date: 2010-09-15 23:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- tic tac toe
  -- rails
---

I finished the Tic Tac Toe on Rails 3 today.  There are still some unconventional code that should be translated to Rails.  Things like generating HTML from helper methods where I can use the tag helpers instead.  Here are some of the gotchas I experienced.

## Rails 3 lib directory does not autoload

This is an [intentional](https://rails.lighthouseapp.com/projects/8994/tickets/5218-rails-3-rc-does-not-autoload-from-lib) feature in Rails 3 and was introduced to make Rails "behave more closely" to Ruby projects.  If you want your application to behave like it did in Rails 2.x, just add the *config.autoload_paths* in the application.rb file.

{% highlight ruby %}
module RailsApp
  class Application < Rails::Application
    config.autoload_paths += %W(#{config.root}/lib)
  end
end
{% endhighlight %}

## Rails autoload convention - unfamiliar territory

I guess I was unfamiliar with the way Rails loaded up the game engine module in my lib directory (once I got the autoload working).  I had my own config class that was part of the game engine to support configurations.  The problem was that the classes under the game engine module needed to load up in a certain order (I think that might be a smell).  There is a constant in one of the files that assumed another file instantiated a class and set it to that constant.  So I scrapped that configuration set up and use Rails instead.  I didn't quite understand where to put constants as things have slightly shifted in Rails 3 config, so I placed it in the environment.rb file:

{% highlight ruby %}
TTT_CONFIG = {
  :boards  => { :'3x3' => { :active => true, :cache => :hash, :on => "3x3.jpg", :off => "3x3_dim.jpg" },
                :'4x4' => { :active => true, :cache => :mongo, :on => "4x4.jpg", :off => "4x4_dim.jpg" } },
  :pieces  => { :o => 'O',
                :x => 'X' },
  :players => { :human => { :value => "human",       :on => "player_human.jpg",    :off => "player_human_dim.jpg" },
                :easy  => { :value => "easy",        :on => "player_easy_cpu.jpg", :off => "player_easy_cpu_dim.jpg"},
                :med   => { :value => "med",         :on => "player_med_cpu.jpg",  :off => "player_med_cpu_dim.jpg"},
                :hard  => { :value => "unbeatable" , :on => "player_hard_cpu.jpg", :off => "player_hard_cpu_dim.jpg"} },
  :cache => {}
}
{% endhighlight %}

## XSS Protection is on by default

This was a brand new problem for me in Rails.  As I've said in the beginning of this post, I'm generating HTML (code borrowed from the WEBrick version of Tic Tac Toe) and of course, when the HTML was handed back to the view, it converted the HTML to be safe.  In order to resolve this problem, I called *html\_safe* after each method call in erb.

{% highlight erb %}
<%= options_for_board.html_safe %>
{% endhighlight %}

What I should really do is take advantage of Rails tag helpers and some CSS.  As [Craig](http://twitter.com/demmer12) pointed out, the mouse events that I've implemented in JavaScript can be done in CSS.  If only I had some more time, I could try it with CSS...

## Protect from Forgery

I'm not sure if this was not on by default in Rails 2.x, but it is for Rails 3.  In the ApplicationController, it's the very first thing in the class.  Since this is just a game, I commented it out, but if I were working on a real app, I would not do this and find another way.  By commenting this out, I'm probably doing something wrong.

I had fun with Rails 3.  I hope to work on it more and I plan to read [Diapora project](http://github.com/diaspora/diaspora) soure code which happens to be Rails 3.
