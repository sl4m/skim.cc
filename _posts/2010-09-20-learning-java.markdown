---
layout: post
title: learning java
date: 2010-09-20 23:00:00 -05:00
categories:
  -- software craftsmanship
  -- java
  -- junit
  -- continuous learning
---

*Note:* I took some time off, and now I'm back in action.

I tried reading Effective Java, but quickly realized I needed to step back and re-read the basics.  So it was a good thing Colin mentioned another book, Agile Java.  When I briefly read the first chapter, I knew this was the book to start out.  Here are some notes so thus far.

### Java is included in Mac OS X by default

Apple makes it super easy to start developing in Java and provides the latest JDK 1.6 in Snow Leopard.  I thought when I was having a JUnit issue, it had something to do with the default installation of Java, but it was not.

### Classpaths

The author talks about the classpath as being "one of the more confusing aspects of working with Java".  I couldn't agree more.  When calling *javac* (java compile command) or *java*, you may need to provide classpaths.  When having more than one classpath, a delimiter is used to separate each path.  For whatever reason, the delimiters are different when working in Windows and Unix systems.  Windows requires you to separate paths using a semi-colon, whereas Unix requires a colon.  The book examples default to Windows which I overlooked.  This created some frustrating moments last week.  It's also important to place appropriate quotes around paths with spaces.  This is more of a Windows dilemma (e.g., Program Files).

##### Windows

{% highlight text %}
javac -cp .;c:\some\path\to\junit.jar ClassTest
{% endhighlight %}

##### Unix

{% highlight text %}
javac -cp .:~/some/path/to/junit.jar ClassTest
{% endhighlight %}

Specifically for Mac OS X, if you place the jar files in /Library/Java/Extensions or ~/Library/Java/Extensions, you do not need to explicitly provide the path.

### A bit of Java History

Charles Nutter recently posted a [great article](http://blog.headius.com/2010/08/my-thoughts-on-oracle-v-google.html) on Oracle vs Google lawsuit and gives great detail about the history of Java.  I did not know Java is an open and closed platform and how Sun unfortunately did not open source the test kit to allow developers to create fully compatible open-source Java.  Charles further piqued my interest in Java and I look forward to learning more about it.

### Java REPL

There's a Java REPL called [Beanshell](http://www.beanshell.org/home.html).  I can't tell if it's still in active development.  The notes say it works for 1.5, so I'm assuming, it's not, but seems like a nice tool to have when in need to interpret code.

### Uncle Bob's Craftsman Articles

Uncle Bob's [Craftsman articles](http://objectmentor.com/resources/publishedArticles.html) has a lot of information about Java and TDD.  I like the way he story tells about an apprentice's experience.  It only seem natural for an apprentice to read about an apprentice.

### Socket Server in Java

Fortunately, I found an article on writing Socket Server in Java (from Uncle Bob as well), thanks to [Justin's](http://twitter.com/JustinMartinM) [blog post](http://8thlightapprenticeship.blogspot.com/2010/02/day-29.html).  I'll be up all night reading it and try to get this four point story done.

### Java Online Resources

* [Java Docs](http://download.oracle.com/javase/6/docs/api/)
* [JUnit](http://github.com/KentBeck/junit)
