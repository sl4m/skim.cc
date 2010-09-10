---
layout: post
title: practicing prime factors kata
date: 2010-09-09 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- tic tac toe
  -- webrick
---

I spent most of today practicing the [Prime Factors](http://vimeo.com/7762511) kata in preparation for tomorrow's "recital".  I will be performing the kata in front of the other 8th Lighters during the Lunch 'n Learn.  I feel pretty confident about it after working through many times over.  I lost count and can't tell how many times I've done it, but it feels good to know that I can now outpace Uncle Bob ;\-\).  Of course, katas aren't about speed, but about the practice and form.  I think it helps me get into the TDD groove by starting off with nothing, but a test.  This was a fun exercise and I look forward to practicing more katas like the [Bowling kata](http://blog.objectmentor.com/articles/2009/10/01/bowling-game-kata-in-ruby) and continually improve my TDD skills.

For the rest of the day, I worked on finishing up the multiplayer support for WEBrick Tic Tac Toe.  Unfortunately, it was not smooth sailing as there was a small hiccup along the way.  For some reason, WEBrick cookies (or cookies in general) do not like cookie values as *, , , , , , , ,*.  Google Chrome showing me the cookie value is stored correctly, but when retrieving the cookie value on the GET request, it returns as nil.  To resolve the issue, I temporarily replace empty spaces with dashes and revert it back on the GET.

{% highlight ruby %}
# when saved to a cookie
@board.serialize.gsub(/\s/, '-')

# when retrieved from the request
board_state = cookie_value(request, "board_state").gsub(/-/, ' ')
{% endhighlight %}

Now everyone's happy and I ran a simple test - ran an instance of the game on Google Chrome and Firefox and it seems to play independently.  Awesome.  I refactored the servlet as I found some duplicate code and refactored the tests.  This looks ready to be delivered to the customer.  I'll take a look at the code again this weekend just to double check I'm not missing anything while I work on the Rails 3 version.  That's going to be a lot of fun.
