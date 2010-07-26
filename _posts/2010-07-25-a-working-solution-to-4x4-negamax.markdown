---
layout: post
title: a working solution to 4x4 negamax
date: 2010-07-25 23:00:00 -05:00
categories:
  -- software craftsmanship
  -- mongodb
  -- ruby
  -- negamax
---

![TTT 4x4 Negamax](/images/ttt_4x4_negamax.jpg)

I have a working solution for the 4x4 Tic Tac Toe Negamax player.  After a week of [yak shaving](http://skim.cc/2010/07/24/continuous-yak-shaving), I found a way to store the 4x4 Negamax moves into a database (MongoDB) and have it play against any player including itself.

It required the following:

* Patience
* Negamax algorithm with memoization with a dash of hash buffering
* MongoDB indexing (super easy to create)
* Patience
* A supercomputer (or decent dual-core)

Initially, I was only going to grab the positions 0, 1, 4, 5 and get the other positions by rotating/flipping the board.  I found out during the process, however, that it was not needed and memoization pretty much took care of the rest.  Once I had 0, 1, 4, 5, it was very easy to get the other 12 positions.

{% highlight text %}
 0 | 1 | 2 | 3    3 | 2 | 1 | 0
---+---+---+---  ---+---+---+---
 4 | 5 | 6 | 7    7 | 6 | 5 | 4
---+---+---+---  ---+---+---+---
 8 | 9 | 10| 11   11| 10| 9 | 8
---+---+---+---  ---+---+---+---
 12| 13| 14| 15   15| 14| 13| 12

 12| 13| 14| 15   15| 14| 13| 12
---+---+---+---  ---+---+---+---
 8 | 9 | 10| 11   11| 10| 9 | 8
---+---+---+---  ---+---+---+---
 4 | 5 | 6 | 7    7 | 6 | 5 | 4
---+---+---+---  ---+---+---+---
 0 | 1 | 2 | 3    3 | 2 | 1 | 0

 3 | 7 | 11| 15   15| 11| 7 | 3
---+---+---+---  ---+---+---+---
 2 | 6 | 10| 14   14| 10| 6 | 2
---+---+---+---  ---+---+---+---
 1 | 5 | 9 | 13   13| 9 | 5 | 1
---+---+---+---  ---+---+---+---
 0 | 4 | 8 | 12   12| 8 | 4 | 0

 0 | 4 | 8 | 12   12| 8 | 4 | 0
---+---+---+---  ---+---+---+---
 1 | 5 | 9 | 13   13| 9 | 5 | 1
---+---+---+---  ---+---+---+---
 2 | 6 | 10| 14   14| 10| 6 | 2
---+---+---+---  ---+---+---+---
 3 | 7 | 11| 15   15| 11| 7 | 3
{% endhighlight %}

I have 14,080,239 documents in my MongoDB.  This includes 3x3 and 4x4 board states and roughly equates to about 1.04GB.  It took an estimate of 5-6 hours to populate the database, running two different games at the same time on a blank board.  It pretty much maxed out my CPU.  I was getting a little worried the mongod process was going to max out my memory, but fortunately it did not.  I think it went all up to 2.5GB in terms of memory usage.  I'm storing three fields to each document:

{% highlight ruby %}
document = {"board" => "OXOXOXOXO", "piece" => "O", "score" => 1}
{% endhighlight %}

Initially when running the process, it was storing the documents at a slow pace of about 100 documents/sec.  I read on [mongodb-user](http://groups.google.com/group/mongodb-user) Google Group that it was [not recommended to create the index before a mass data load](http://groups.google.com/group/mongodb-user/browse_thread/thread/29c03d7379b78be0/c7d6d0c83cbfc0f2?lnk=gst&q=index#c7d6d0c83cbfc0f2).  I didn't think I was going to have 350 million documents so I created it by using a simple command in an IRB session:

{% highlight text %}
ruby-1.9.2-preview3 > coll.create_index("board")
 => "board_1" 
{% endhighlight %}

Wow.  It significantly boosted the performance.  It was storing at a rate of about 2000+ documents/sec and it kept increasing.  Now since I created the index early on, when new documents are written to the database, it also indexes them at the same time.  I still think creating the index before will be faster than creating it after.  I needed the performance right away since writing 14 million documents can take some time.

My RSpec test suite passed and I checked in the latest code.  I'm happy to finally move this story from Working phase to Complete.  Now on to the UI story...
