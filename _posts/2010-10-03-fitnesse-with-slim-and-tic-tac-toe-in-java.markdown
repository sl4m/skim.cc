---
layout: post
title: fitnesse with slim and tic tac toe in java
date: 2010-10-03 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- yak shaving
  -- java
  -- stories
  -- fitnesse
  -- slim
  -- acceptance tests
  -- tic tac toe
---

My FitNesse with SliM story is complete.  Albeit, not creating many acceptance tests for the Limelight styles parser, I found the FitNesse's DSL to be a tad difficult.  Fortunately, Uncle Bob posted the SliM overview video, where I repeatedly watched the video to get every little detail.  I had problems defining the classpath, figuring out where fixtures are supposed to go, figuring out how to implement the style table, and figuring out how to compare expected and actual.  

### Fixtures

I ended up putting the fixture in a separate package under the main package.  The fixture class name ended up being the same as the class name that contains the main method.  I'm not sure what's the convention for this sort of thing, but it works, so I'm happy.

### Expected and Actual Comparison

I initially tried to approach the problem by doing a file comparison, but could not find a standard Java library that does file comparison.  I ended up with a solution where the expected Java code are stored in files.  Upon comparing expected and actual, the appropriate file is read and stored into a string, then a string comparison is made.  This worked out to be the best way.

## Tic Tac Toe in Java

My Tic Tac Toe in Java implementation is complete.  The time I lost working more on FitNesse, I gained back by completing this implementation earlier than my estimation.  Since I've already went through the trials and tribulations of Tic Tac Toe, it was not difficult to write the game in another language.  Nothing I've written in Ruby for my Tic Tac Toe, could I not port into Java.  I was rather surprised at how easy it was to port.  One thing I ran into trouble was mocking standard input/output.  I ended up with a solution that I'm somewhat pleased.  The standard input is still a little icky, but I managed to create a workaround solution.  Take a look:

#### StdIn mocking

{% highlight java %}

public ByteArrayInputStream createInputStream(String string)
{
  return new ByteArrayInputStream(string.getBytes());
}

public StdUI createStdUI(String string)
{
  ByteArrayInputStream bs = createInputStream(string);
  return new StdUI(bs, new MockPrintStream());
}
{% endhighlight %}

#### StdOut mocking

{% highlight java %}

// MockPrintStream.java

import java.io.PrintStream;

public class MockPrintStream extends PrintStream
{
  public MockPrintStream()
  {
    super(new MockOutputStream());
  }

  public void write(int some)
  {
  }

  public void println(String message)
  {
  }
}

// MockOutputStream.java

import java.io.OutputStream;

public class MockOutputStream extends OutputStream
{
  public void write(int something)
  {
  }
}
{% endhighlight %}

The code is available on my GitHub [repo](http://github.com/sl4m/tic_tac_toe_java).
