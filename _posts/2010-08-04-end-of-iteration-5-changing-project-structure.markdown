---
layout: post
title: end of iteration 5, changing project structure
date: 2010-08-04 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- stories
  -- webrick
---

## End of Iteration 5

Today was the end of Iteration 5 meeting where Micah and I discussed the stories that were assigned for the iteration.  Finally, I'm back to completing a full iteration.  Overall, he seemed happy with the stories and I moved each one to the archive.  He did note the cosmetic issue with the Limelight Tic Tac Toe program.  I need to figure out how to make the background of the pieces transparent and not white as they are now.  I'm adding that to my todo list.  Another thing on the list is to re-organize the project structure which I talk about below.

For iteration #6, one of the stories calls for making my WEBrick Tic Tac Toe look exactly like my Limelight Tic Tac Toe.  I still need to read up on how to ping pong actions between user and servlet once the board is displayed on the page.  I think I have an idea though.

## Changing Tic Tic Toe Project Structure

I spent some time re-organizing the project structure.  I thought if I organize it in the beginning of the new iteration, it will help improve my workflow as I'm constantly looking up different classes, specs, and such.  It'll also allow me to run certain tests that are specific to what I'm adding/changing.  Of course, I will run the entire suite once I'm ready to commit the code.

This is what the new project structure looks like now:

{% highlight text %}
[master][~/local/git/tic_tac_toe_ruby] ls -l
total 24
-rw-r--r--  1 skim  staff   758 Aug  4 19:12 README.md
-rw-r--r--  1 skim  staff   239 Jul  8 12:06 Rakefile
drwxr-xr-x  4 skim  staff   136 Aug  4 16:52 assets/
drwxr-xr-x  4 skim  staff   136 Aug  4 16:43 console/
drwxr-xr-x  4 skim  staff   136 Aug  4 16:45 game_engine/
drwxr-xr-x  4 skim  staff   136 Aug  4 14:27 limelight/
-rw-r--r--  1 skim  staff  1791 Jul 26 13:55 ttt.iml
drwxr-xr-x  4 skim  staff   136 Aug  4 16:40 webrick/
{% endhighlight %}

StdUI is now under console, Limelight under limelight, and WEBrick under webrick.  The Tic Tac Toe engine sits in game_engine, and assets contains the images that currently drive Limelight.  Under each UI, there is a lib and spec folder.  I'm liking the new project structure and hopefully it'll meet my needs.

After working through the project structure changes, I noticed a few good things that came out of it (other than the fact that it's neatly organized):

* Discovering [cruft](http://en.wikipedia.org/wiki/Cruft)
* Learning more about $LOAD_PATH
* Learning more about Limelight's handle on image paths

I found several cruft that were not removed when I extracted classes about a month ago.  These came up when running the game engine specs.  I'm glad to be removing the cruft, because really who needs 'em!  There were some headaches when trying figuring some $LOAD_PATH issues, but through the small headaches, I have a better understanding about what I need to do for a future project.  Finally, since my Limelight UI utilizes images, I had trouble figuring out the cwd (current working directory) for background_image and hover.background_image.  I had initially set them to "images/background/...", and tried adding the new images path to the $LOAD_PATH, but it doesn't read from there at all.  I'm not sure what I was thinking, but I thought it would look in the $LOAD_PATH.  I quickly fired up Limelight Playbills to load up the Limelight docs and found out in the Background tutorial that "the filename of the image should be relative to the root directory of the Production."  Bingo.  I quickly converted all paths by using an instance variable I created from Production, but ran into a little problem.  Styles.rb does not seem to understand the production object, so I had to hardcode in the new paths 

This is probably the biggest [commit](http://github.com/sl4m/tic_tac_toe_ruby/commit/61bef205545b3d8940e9eaedde0d2d667b9f6371) I've ever made to GitHub, albeit its non-feature change; it's nice to having a clean project again.

## "Spicy Tuna" Hand Roll Mocks

I probably should've stopped blogging after the project structure topic, but I wanted to talk a bit on hand rolling mocks.  Some of my RSpec tests needed a mock of an instance of WEBrick::HTTPRequest which is created on the fly when running WEBrick::HTTPServer.  I ended up hand rolling my own mock because it was much easier than using RSpec's mock.  Let's take a look at why it was easier.  The mock was created in the before(:each) block for setup convenience.  Here is the RSpec way:

{% highlight ruby %}
@request = mock("request")
@request.should_receive(:query).and_return(hash = mock("hash"))
hash.should_receive(:[]).with('board').and_return('3x3')
hash.should_receive(:[]).with('player_o').and_return('human')
hash.should_receive(:[]).with('player_x').and_return('unbeatable')
{% endhighlight %}

Something doesn't taste right about the mock code above.  First, I'm actually creating two mocks: one for the request and another for the query which contains a hash.  Second, it's expecting hash to receive :[] message with three different arguments.  Some of my test won't use all three, so it'll fail on "should receive".  Let's take a look at when you hand roll your own mock:

*Note:* Thanks to Colin for pointing me in the right direction to create a class instead of creating an object and using *instance_variable_set* to create the query ivar.

{% highlight ruby %}
class MockRequest
  attr_accessor :query
  def initialize
    @query = {}
  end
end

describe BoardServlet do
  before(:each) do
    @request = MockRequest.new
    @request.query['board'] = '3x3'
    @request.query['player_o'] = 'human'
    @request.query['player_x'] = 'unbeatable'
  end
end
{% endhighlight %}

Doesn't that look much cleaner?  It flows better than using RSpec mock.  I think there's a special place for hand rolling your own mocks, but I don't think it should be done all the time.  RSpec mocks do a great job by itself.
