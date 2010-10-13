---
layout: post
title: http server in java demoed, faking out web calls
date: 2010-10-12 23:30:00 -05:00
categories:
  -- software craftsmanship
  -- java
  -- http server
  -- apprenticeship challenge
  -- yak shaving
  -- ruby
  -- rspec
---

## Challenge Demo

I demoed the HTTP server to Micah today and it went well.  We looked at the code and he pointed out some smelly areas.  For instance, my Response class was doing most of the work.  The Request class would massage the data coming in from the client's socket and the Response will do everything else.  Micah pointed out that my construct200Response, construct404Response methods should be calling Response class to "construct" a response based on the status code, but everything was all in the Response class.  Oops. Overall, the server worked as intended and the requirements were met.  The last thing he asked was what would I do if I were to extend the HTTP server.  Here's a list of what I do:

* support all request methods (e.g., HEAD, POST, PUT, DELETE, TRACE, CONNECT)
* support all status codes
* support all current MIME types
* add more header fields to the Response (e.g., Server, Content-Encoding, Date)
* make the Response class more modular

One final thing that I didn't quite understand was how to read a GET request properly.  My current implementation looked at the first 1024 bytes and that's it.  I tried to create a while loop and wait for -1.  However, it does not work that way.  -1 is returned from an InputStream read method is there's a end of string/line situation, but not for a socket InputStream.  The only time it'll return -1 is if the socket is closed.  So after talking through with Micah, the correct way to read a GET request is when you reach two carriage return line feeds (\\r\\n).  You might ask, what about the entity body?  If you recall the entity body is separated by two carriage return line feeds from the request headers.  Fortunately, the entity body does not appear for GET requests.  If an entity body appears, the client's socket should provide the Content\-Length.

So here's the breakdown:

1. A GET request will not have an entity body, so look for Content\-Length of zero or two carriage return line feeds (whichever comes first).
2. On other requests that are allowed to have entity bodies (e.g., POST), look for Content\-Length and use that value to count the entity body coming in.

This should be a pretty sure guarantee, you have the entire request.

## Faking out web calls in specs

Following collective ownership, I'm glad to complete changes to specs I've written with Matt when working on a Rails project.  What we've naively done is make direct calls to an actual server.  This is a big no no and we should have faked those calls.  For instance, if I were on the train and did not have internet and wanted to run the specs, I was out of luck.  All of those tests relying on connecting to the server were going to fail.  So I basically swapped out the Net::HTTP instance for a fake HTTP and when the post method was called, it will return a fake response.  This worked for the majority of the tests, but I ran into a problem trying to fake out Net::HTTP for a class method.  In order for this fake to work, I need a hold of the instance of class I'm testing.  Unfortunately, the class method was creating an instance of this class and storing it in a local variable which I have no access to.  Fortunately (thanks to Colin), there's a way around this.  Having learned about stubs just recently (vs. mocks), this adds a whole new cool to stubs.

{% highlight ruby %}
it "does something" do
  some_class = SomeClass.new
  some_class.https = FakeHTTPModule
  SomeClass.stub!(:new => some_class)
  SomeClass.class_method
end
{% endhighlight %}

As you can see in the code above, what I'm trying to do is create an instance of the class I want to test (e.g., SomeClass) and set the FakeHTTPModule to https attribute.  This FakeHTTPModule has the fake post method which some\_class will call.  Now in the class\_method, it instantiates SomeClass and stores it in a local variable.  I want to get a hold of this local variable to set https to the fake module.  With this stub technique, it's possible to do this.

## Small Limelight Project for SCNA

Up next, Micah and I will be working on a simple Limelight project for SCNA conference.  I look forward to doing some awesome pair programming and working in Ruby again (although I really enjoyed Java).  We already have some ideas for what we want to do for this project.  To give you a hint, I'm looking for a sound effect for the [Solari departure board](http://en.wikipedia.org/wiki/Solari_departure_board).  More on this later. 
