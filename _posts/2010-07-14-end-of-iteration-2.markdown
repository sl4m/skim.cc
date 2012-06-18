---
layout: post
title: end of iteration 2
date: 2010-07-14 16:00:00 -05:00
categories:
  -- software craftsmanship
  -- ux
  -- nosql
---

## NoSQL spike

Today I looked over some of the NoSQL data stores out there, specifically, Redis, CouchDB, and MongoDB.  In the end, I chose MongoDB to store the possible moves for the 4x4 board.  Why MongoDB?  Just personal preference.  I said yesterday I wouldn't use it because I didn't have any available 8th Lighters to help me, but honestly the docs out there are well written and give you all the information you need to get started.

Speaking of which, I'll be using these links to guide me to Mongo heaven:

* [MongoDB Quickstart](http://www.mongodb.org/display/DOCS/Quickstart)
* [Mongo gem](http://rubygems.org/gems/mongo)
* [Mongo gem doc](http://api.mongodb.org/ruby)
* [Try MongoDB](http://try.mongodb.org/)
* [MongoDB Ruby Koans](http://github.com/chicagoruby/MongoDB_Koans)

I read the MongoDB Quickstart guide to learn how to install MongoDB to my MacBook Pro via homebrew:

{% highlight text %}
brew install mongodb
{% endhighlight %}

Be sure to have the latest brew formulas or you might get an older version of MongoDB.  To do so, run these [commands](http://wiki.github.com/mxcl/homebrew/tips-n-tricks): 

{% highlight text %}
[/usr/local] git init
Initialized empty Git repository in /usr/local/.git/
[master][/usr/local] git remote add origin http://github.com/mxcl/homebrew.git
[master][/usr/local] git pull origin master
From http://github.com/mxcl/homebrew
 * branch            master     -> FETCH_HEAD
{% endhighlight %}

Install mongo gem:

{% highlight text %}
gem install mongo
{% endhighlight %}

Create a folder and kickoff an instance of MongoDB:

{% highlight text %}
[~] mkdir -p /data/db
[~] mongod
mongod --help for help and startup options
Thu Jul 15 00:31:03 Mongo DB : starting : pid = 82628 port = 27017 dbpath = /data/db/ master = 0 slave = 0  64-bit
Thu Jul 15 00:31:03 db version v1.4.4, pdfile version 4.5
Thu Jul 15 00:31:03 git version: 9dcac11bd72c7cb34ca278313f033efcdd4908eb
Thu Jul 15 00:31:03 sys info: Darwin erh2.10gen.cc 9.6.0 Darwin Kernel Version 9.6.0: Mon Nov 24 17:37:00 PST 2008; root:xnu-1228.9.59~1/RELEASE_I386 i386 BOOST_LIB_VERSION=1_37
Thu Jul 15 00:31:03 waiting for connections on port 27017
Thu Jul 15 00:31:03 web admin interface listening on port 28017
{% endhighlight %}

In another Terminal instance, run this simple example to test out the MongoDB installation and mongo ruby driver:

{% highlight ruby %}
require 'rubygems'
require 'mongo'

include Mongo

db = Connection.new.db('ruby-mongo-examples')
coll = db.collection('test')

# Erase all records from collection, if any
coll.remove

# Insert 3 records
3.times { |i| coll.insert({'a' => i+1}) }

puts "There are #{coll.count()} records in the test collection. Here they are:"
coll.find().each { |doc| puts doc.inspect }

# Destroy the collection
coll.drop
{% endhighlight %}

See the results

{% highlight text %}
[~/local/ruby] ruby mongo_simple.rb

**Notice: C extension not loaded. This is required for optimum MongoDB Ruby driver performance.
  You can install the extension as follows:
  gem install bson_ext
  If you continue to receive this message after installing, make sure that the
  bson_ext gem is in your load path and that the bson_ext and mongo gems are of the same version.
There are 3 records in the test collection. Here they are:
{"_id"=>BSON::ObjectID('4c3e9de8cc9ed64326000001'), "a"=>1}
{"_id"=>BSON::ObjectID('4c3e9de8cc9ed64326000002'), "a"=>2}
{"_id"=>BSON::ObjectID('4c3e9de8cc9ed64326000003'), "a"=>3}
{% endhighlight %}

I didn't get much further than that.  I will be working on the MongoDB Ruby Koans tomorrow to get a better understanding of MongoDB and usage patterns.

## End of Iteration 2 Meeting

I sat down with Micah (customer) to go over the two stories I was assigned for Iteration 2:

* Implement 4x4 board
* Create UI mockups
* Improve performance of Negamax player in 4x4 board (spike)

I think overall he was satisfied with what I've done to the 4x4 board and UI mockups.  I estimated the new stories to be about five points each:

* Implement UI mockups
* Improve performance of Negamax player in 4x4 board

There are still a couple of stories in the Backlog which I'll work on in Iteration 4.  But for this new iteration, I will be focusing on the two stories.
