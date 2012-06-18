---
layout: post
title: eventmachine
date: 2010-10-25 23:30:00 -05:00
categories:
  -- client
  -- ruby
  -- eventmachine
---

Today, Li\-Hsuan and I finished up an [EventMachine](http://github.com/eventmachine/eventmachine) task we started on Friday.  We were testing and implementing a way for the server to send an errorback (a callback for errors) if the desired port for the server is occupied.  We thought TCPServer occupied a port, but in fact it did not.  I'm not sure what it was doing.  We ended up creating EventMachine servers back to back and was able to catch an exception which then surfaced up to the calling code.  After completing the task, we were given another task where Doug wanted us to handle exceptions and have them surface up via errorback for method calls that do not exist.  To make sense in all of this, there are two "connections".  We can call them server and client, but both sides can send/receive messages.  Similar to DRb, Doug implemented a way for both server and client to call each other's methods.  If the client calls a method that does not exist locally, it automatically send the message to the server and attempt to run that message on the server side.  There are two ways of which this can happen:

1. Client truly wants to call Server's method and calls it.
2. Client accidentally mispelled local method.

At the end of today, we were able to finish pretty much the entire implementation except when server makes calls to client's methods.  We'll need to talk to Doug about this.

## A little introduction to EventMachine

This is Ruby's evented I/O, similar to Node.js.  It's designed around the [Reactor pattern](http://en.wikipedia.org/wiki/Reactor_pattern) and reminds me of the Socket Service and Executor Service I implemented for the HTTP server in Java, except way faster and [C10k](http://en.wikipedia.org/wiki/C10k_problem) aware (although not a counter solution to it).  It encapsulates the socket level, so you can focus on the application logic and is designed to be used to create both server and client.

*EventMachine::run* is used to run the event loop.  It does block, so a callback is needed to terminate the event loop.  *EventMachine::stop\_event\_loop* is used to stop the event loop.  All open connections will cease and close.

EM is an alias of EventMachine and can be used interchangeably.  There are other aliases in EventMachine.

{% highlight ruby %}
class Echo
  def post_init
    puts "Hello"
  end

  def receive_data(data)
    p data
  end
end

EventMachine::run do
  EventMachine::start_server '127.0.0.1', 8081, Echo do |connection|
    # connection is EventMachine::Connection + Echo module
  end
end
{% endhighlight %}

The code above is an example of a simple server started in EventMachine.  Echo is a handler, a key component in EventMachine to handle particular network protocols.  This module magically mixes in with an instance of *EventMachine::Connection* and is returned in the start_server block.

{% highlight ruby %}
# code from EventMachine wiki

module Echo
  def receive_data(data)
    p data
  end
end

EventMachine::connect '127.0.0.1', 22, Echo
{% endhighlight %}

For connections, handlers can be blocks/procs, modules or classes.  In the example above, the module Echo is used to handle connections on localhost port 22.

I'm not sure if I made any sense in this introduction, but there's a lot to say about EventMachine and what I briefly wrote here is just touching the surface.  It has deferables, periodic timer, different protocol support, error handling, etc.

### References

* EventMachine [GitHub repo](http://github.com/eventmachine/eventmachine)
* EventMachine [rdoc](http://eventmachine.rubyforge.org/)

