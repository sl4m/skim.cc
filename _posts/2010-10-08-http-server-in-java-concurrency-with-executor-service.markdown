---
layout: post
title: http server in java - concurrency with executor service
date: 2010-10-08 23:30:00 -05:00
categories:
  -- software craftsmanship
  -- yak shaving
  -- java
  -- http server
  -- apprenticeship challenge
  -- concurrency
---

{% highlight java %}
public void listen()
{
  requestExecutorStart();
  while (!requestExecutor.isShutdown() && executorRunning)
  {
    final Socket socket = acceptConnection();
    if (socket != null)
    {
      processConnection(socket);
    }
  }
}
{% endhighlight %}

This Java exception bit me in the dust today: SocketException.  According to the Javadoc, when ServerSocket's close method is called while any thread is currently blocked by the accept method, it will throw the SocketException.  When I was testing SocketService, I had this exception thrown, but could not figure out what was throwing it.  Javadoc is your friend.  I caught the exception and moved on.  Fortunately, Micah had some time to pair with me.  We were able to finish the implementation of the SocketService.  I went over what I needed to finish and he seemed to agree with everything I said.

### HTTPHandler: Request and Response

The SocketService will handle all client requests and have its ExecutorService create and run the tasks passing the socket to the handler.  The handler will read the socket's request using its getInputStream to read the request in full, parse it, and create a response to write to the socket's getOutputStream.  I believe at this point, each task is self-contained and will not need multi-threading.  Unfortunately, there are some gotchas that I'm not aware of, sounds funny I know.  Micah said there will be some things I will encounter.  I hope I won't see too many.

## Lunch n' Learn - git

The new Lunch n' Learn series is from Craig.  We went over the basics of git - installation, links to different references, gitconfig.  I learned several things new in today's session like gitconfig color ui and bash autocompletion.  I look forward to the next session which will be after [SCNA](http://scna.softwarecraftsmanship.org/).  I could use some more git skills.
