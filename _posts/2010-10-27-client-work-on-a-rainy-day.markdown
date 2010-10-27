---
layout: post
title: client work on a rainy day
date: 2010-10-27 08:30:00 -05:00
categories:
  -- client
  -- ruby
  -- eventmachine
---

Yesterday, I had an early start in the morning.  We had a bi\-weekly iteration meeting with the client where we demoed stories we've been working on the past couple of weeks.  It was nice to see the story Li\-Hsuan and I worked on demoed to the client albeit how little the feature was.

Li\-Hsuan and I continued to work on several EventMachine related tasks.  I have to say, there's something to be said about EventMachine's method calling [convention](http://eventmachine.rubyforge.org/EventMachine.html).  Usually, when I see a constant after a constant with two colons (e.g., EventMachine::), I usually see a class or module.  But EventMachine likes to use '::' to call module methods.  You could simply run the same method using the dot notation, but the documentation and all example code uses '::'.  Perhaps, I've not read enough Ruby code, but it seems a little odd.

{% highlight ruby %}
EventMachine::run {
}

EventMachine.run {
}
{% endhighlight %}

So when attempting to mock EventMachine, at first I didn't know how to do it.  But after trial and error, it's the same way as any other type of mocking:

{% highlight ruby %}
EventMachine.should_receive(:stop_server).once
{% endhighlight %}

During the entire time working on EventMachine, we were using Ruby MRI 1.8.7, but this library will be used on JRuby.  So we switched to JRuby, installed the gem, and saw a lot of our tests fail.  We found out from Doug, the Java implementation is not quite the same as its C extension sister.  We ended up building the gem from the GitHub repo.

{% highlight text %}
[~/local/git/em-gem] rake java:gem
{% endhighlight %}

Some tests still failed after installing the edge version, but we were able to make them pass and checked in the code.  There's still some more work to be done, so we will be sitting with Doug today to go over some of the new tasks.
