---
layout: post
title: socket server in java
date: 2010-09-22 21:00:00 -05:00
categories:
  -- software craftsmanship
  -- yak shaving
  -- java
  -- junit
---

*Note:* Here's the two day recap while I dive deeper into the Java programming language.

I'm reading the [source code](http://github.com/slagyr/mmsocketserver_java) Micah written for Socket Server in Java.  It looks similar to the code for the Craftsman articles (6\-9) on [Object Mentor](http://objectmentor.com/resources/publishedArticles.html).  As I'm reading the articles, I'm understanding how to code is being driven with tests and the communication involved between the two programmers as they ping pong pair program.  Here are some observations:

### Anonymous Inner Class to Implement an Interface

{% highlight java %}
connectionCounter = new SocketServer()
{
  public void serve(Socket s)
  {
    connections += 1;
  }
};
{% endhighlight %}

This is probably the first time I'm seeing this.  It looks similar to passing a block to a Ruby method, but not the same idea.  *SocketServer* is an interface which require a serve method to be implemented.  This block of code defines the serve method required for the *SocketServer* interface and creates an instance of the anonymous inner class.  Pretty interesting stuff.

### Importing Java Libraries

I've noticed sometimes, developers will use an '\*' at the end of an import statement to indicate that they would like all libraries.  I wonder when to properly use the '\*' (e.g., more than 3\-4 packages?) and if it's considered lazy to immediately use '\*' when only using one package.

{% highlight java %}
import java.io.*
import java.net.Socket;
{% endhighlight %}

### Intentional Programming

I was unaware of the name of the [concept](http://en.wikipedia.org/wiki/Intentional_programming) used when calling code that does not yet exist.  This is commonly used in TDD.  You write code that calls a method that does not yet exist, run the test to make it fail (red), write the new method, run the test to make it pass (green), and refactor if necessary.

### Race Condition

I kept hearing this [term](http://en.wikipedia.org/wiki/Race_condition) being thrown around in the office, but didn't know what it was.  It basically occurs in multi-threaded environments.  Asychronous events need are sensitive to the order of execution.

### Running tests multiple times

While it might not be necessary to run single-threaded tests multiple times, multi-threaded tests should probably run be multiple times.  In the case of Alphonse in the Craftsman articles, he saw a test pass 7/10 times.  He witnessed the race condition.

### Mock Object Pattern

This is a [pattern](http://en.wikipedia.org/wiki/Mock_object) I'm pretty comfortable with, after using it many times via RSpec.  The act of mimicking real objects with simulated ones to test behavior.

### Creating methods to make testing easier

This is an interesting technique which I learned in the beginning of my apprenticeship.  Similarly, in Ruby, changing an attribute from a read-only variable to a read-write variable to make testing easier is allowed.  As developers, we trust each other that we will not be changing the attribute's value directly.

## Implementing the Socket Server with Micah

I missed this story in my last iteration, but made it a priority to get it done first.  

As I was reading the articles and the source code to understand how socket servers were created, Micah stopped by and paired with me briefly.  In what seemed like a matter of minutes, we created a simple socket server that displays a message with the current time.  I'm both sad and embarassed how easy this was.  Sad because I spent so much time reading material after material trying to understand how to implement a socket server.  I was also trying to play catch up and re-learn how to write in Java and what methods to use.  Embarrassed because the customer paid 6 points to have this story complete, where it should have really taken 1-2 points.  Micah mentioned that I'm probably reading too much.  This is true.  I will try to focus more on spiking and then test drive the stories.

I finished the socket server at the end of the day by test driving it.  I had several issues mimicking a client socket connection to the server.  Fortunately, the material I learned from the Craftsman articles gave me an idea to create a thread and loop attempts to create a client socket connection until the connection is made.

## Goodbye Iteration #9, Hello Iteration #10

As mentioned above, I missed my socket server story, so it's now in Iteration #10.  Other stories include performing the Bowling Kata in Java and creating an executable jar file that will read a Limelight styles.rb file and output equivalent Java code.  The former story does not sound too difficult.  I have experience performing Prime Factors kata in front of an audience and I've seen Bowling Kata on the web, so I'll do some research.  The latter story, however, sounds a bit tough.  The Limelight styles.rb code looks similar to CSS or object literals in JavaScript.  This will require some parsing and understanding what the Java code equivalent looks like.  I'm going to have to do a lot of spiking.  I wonder if this code will be used in the Limelight source?
