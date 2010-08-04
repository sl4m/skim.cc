---
layout: post
title: webrick - part 4
date: 2010-08-04 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- stories
  -- webrick  
---

## Spicy Tuna Hand Roll Mocks

Some of my RSpec tests needed a mock of an instance of WEBrick::HTTPRequest which is created on the fly when running WEBrick::HTTPServer.  I ended up hand rolling my own mock because it was much easier than using RSpec's mock.  Let's take a look at why it was easier.  The mock is created in the before(:each) block for setup convenience.  Here is the RSpec way:

{% highlight ruby %}
@request = mock("request")
@request.should_receive(:query).and_return(hash = mock("hash"))
hash.should_receive(:[]).with('board').and_return('3x3')
hash.should_receive(:[]).with('player_o').and_return('human')
hash.should_receive(:[]).with('player_x').and_return('unbeatable')
{% endhighlight %}

Something doesn't taste right about the mock code above.  I'm actually creating two mocks: one for the request and another for the query which contains a hash.  Another problem is that it's expecting hash to receive :[] message with three different arguments.  Some of my test won't use all three.  One test will use just the 'board' argument while another will use 'player_o' and 'player_x' arguments.  There has to be a better way...and there is.  Let's roll up our sleeves and create a hand roll mock:

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

Doesn't that look much cleaner?  It flows better than using RSpec mock.  I'm not saying to always hand roll your mocks, but there are some use cases where it's better to hand roll your own.
