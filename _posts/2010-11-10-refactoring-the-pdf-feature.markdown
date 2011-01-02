---
layout: post
title: refactoring the pdf feature
date: 2010-11-10 08:00:00 -05:00
categories:
  -- client
  -- java
  -- pdf
  -- rails
---

I continued working on the pdf library from Monday and finally completed it, creating a decent set of tests.  With the tests now in place, I was able to refactor the code and have confidence that the changes I made didn't break existing functionality.  I then proceeded to implement the pdf template into the Rails project, replacing old code with the new.  I fiddled around with the ant build.xml to create a task to run the unit tests.  Then I created a rake task to run the ant task as part of the *all\_tests* task.  Now when I run *all\_tests*, it will run the unit tests for the Java library first, then specs, and finally cukes.  This will give me confidence that changes I've made on the Java side won't affect tests written on the Ruby side.

I did run into a problem where a particular hash value passed to the Java side was nil.  Unfortunately, I was not expecting null value (Java newbie?) and therefore did not have a test for it.  So I ended up creating tests and a wrapper class that always returns an empty string if the value is null.  This will get rid of the NullException errors and make the library more resilient to nil values.

My next task is to remove the noise in the controller and move it to some models.  Currently, the pdf code is all in the controller and it's a bit noisy.  I've run into this kind of situation several times before and moving it to the model (or even lib) helps cut down the noise.  Controllers should not know too much on how to perform jobs.  The models should know the details and controllers usually delegate to the models or views.  After making the code more DRY, I'll be adding more pdf templates on the Java side.

## 8th Light Hack Night \#2

Last night was the second hack night and Craig and I worked on the Twitter feature from the last time I worked on it.  The way I implemented the feature was a bit hacky and I knew that from the start, so I asked Craig to help me.  To be honest, I basically watched him do his magic via iChat and tried to follow his way of tackling view problems such as this.  In the end, he got it working (took longer than expected) and I went ahead and made the changes to the rest of the bio pages.  While the hacky way took no time at all, I really wanted to learn how to do it the right way.  In this case, diving in to inline styles, HTML source and understand the root of the problem.  I appreciate Craig taking the time to do all of that.

## Other news

I'm trying to learn more Vim commands and use vimperator (on Firefox) and vimium (on Chrome).  While I still reach for the mouse and IDE to help solve bigger problems, I will keep working on using more keyboard shortcuts, using vim exclusively for Ruby/Rails/insert dynamic language projects.  Don't get me wrong, I like [using all sorts of editors](http://skim.la/2010/10/01/redcar-my-new-favorite-text-editor).  I want to be better at all of them, but right now I want to focus on Vim.  It's a great, powerful editor, and every developer, tester should learn how to use it.
