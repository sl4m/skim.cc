---
layout: post
title: rails and node.js - part 2
date: 2010-08-20 22:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
  -- javascript
  -- nodejs
---

I was up pretty late last night working on an issue on the first Rails project I worked on last week.  The flash file implementation worked for all browsers, except Firefox.  Apparently, Gecko based browsers are very strict.  After fiddling with it for many hours on end, the swf_tag just needed an additional parameter and it was happy.

{% highlight text %}
= swf_tag "swf_file_name", :div_id => "div_id_name"
{% endhighlight text %}

I worked on this problem for a long time and all I got was a :div\_id.  I still feel like I learned a lot from this.  The Rails project is using [Haml](http://haml-lang.com/), so I needed to learn how to write some Haml.  The docs are well written and for the most part, I found my answers from the doc.

## Lunch 'n Learn - Node.js and MongoDB

Jim gave his final session on Node.js and introduced MongoDB into the mix.  It was nice to see MongoDB again after having worked on it to store 14 million documents for all possible 4x4 board states.  He presented a JavaScript library called [Mongoose](http://www.learnboost.com/mongoose/) which seems to be inspired by ActiveRecord and we used it to interact with a MongoDB database in Node.js.

{% highlight text %}
npm install mongoose
{% endhighlight %}

Our homework is to write something for our Node.js project that persists the data.  For my project, I will be storing the list of repos for each user.  The only problem I see with persisting the data is when the repository list changes on GitHub (e.g., removing/adding repositories).  I'll need to figure out how to make sure the list that is returned reflects what is on GitHub.

## New tasks for Rails project

Matt and I sat in on a meeting with Paul and the customer to give updates on the project.  I finally understand what we need to do to implement the next feature for the Rails project.  This will be slightly more challenging since we need to authenticate a user coming from another site.  Currently there is no method in the project that allows for this, so we'll need to create it from scratch.  I also noticed the workflow is similar to the previous task, so it should be able to use the class we created after some data abstraction.  I'll have to do some reading to see which pattern might be useful for this situation.  Perhaps, just a simple Module will do the trick.

## Node.js Knockout

The Node.js Knockout is next weekend and our team had a meeting of what we need to learn and tackle in order to create a stellar project and win the [prizes](http://nodeknockout.com/prizes).  I can't tell you what our project idea is yet, but after the weekend, I'll let you know.  Right now, I'll need to read up on HTML5, CSS3, websockets, and Node.js.  It's going to be fun times.  I hope to learn a lot from this challenge.
