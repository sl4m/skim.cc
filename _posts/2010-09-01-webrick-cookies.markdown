---
layout: post
title: webrick cookies
date: 2010-09-01 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- tic tac toe
  -- webrick
---

While searching for some sample code on WEBrick::Cookie, I found a [gist](http://gist.github.com/258527) of a simple library that wraps around WEBrick to make it easier to write WEBrick code.  Reading through the code, I found out how WEBrick::Cookie was instantiated and read back from the response and request, respectively:

{% highlight ruby %}
def add_cookie(name,value)
  @res.cookies.push WEBrick::Cookie.new(name,value)
end
def read_cookie(name)
  @req.cookies.each { |c| return c.value if c.name == name }
  return false
end 
{% endhighlight %}

The invaluable WEBrick documentation Eric Hodel's [website]() explained how cookies are retrieved and set:

> Cookies are read in by WEBrick::HTTPRequest automatically, and are available as an Array from HTTPRequest#cookies. Cookies may be appended to the HTTPResponse#cookies Array when creating a WEBrick::HTTPResponse.

The key to implementing the story "allow multiple players to play TTT at the same time against the computer," is to create cookies for each new session and return back the servlet instance tied to that cookie.  I'll need to store cookies/instances in a hash probably as a class variable (something I'm not fond of using, but apparently it's used for WEBrick servlet instantiations).  

I've implemented the home page in a hokey way where I passed the DocumentRoot as part of the config hash to the new method of WEBrick::HTTPServer:

{% highlight ruby %}
@server = WEBrick::HTTPServer.new({:Port => @port, :DocumentRoot => @document_root})
{% endhighlight %}

However, looking through Hodel's docs, there's another way to do the same thing:

{% highlight ruby %}
@server.mount("/", HTTPServlet::FileHandler, @document_root)
{% endhighlight %}

Fortunately, the latter way is better because it allows me to use a FileHandler config called :HandlerCallback which by definition:

> is a callback which is invoked before the handler for the request.

I plan to create a callback method to create the cookie when the user is on the home page.  This is all still an idea in my head, so I'll need to work on the implementation tomorrow.  Will post updates then.

{% highlight ruby %}
@server.mount("/", HTTPServlet::FileHandler, @document_root, :HandlerCallback => callback_method
{% endhighlight %}
