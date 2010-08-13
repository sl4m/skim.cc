---
layout: post
title: committed my second rails app
date: 2010-08-12 11:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
---

I worked on my second Rails app today.  This time starting from scratch.  Paul wanted me to a build a small Rails app that sends POST form data to a remote server.  Unfortunately, this could not be tested locally since the remote server only supports the staging server with the proper credentials.  So, I had to do what I could to make the app workable.  I didn't know much about sending POST form data to another server, so again I googled around to see if there were any related topics.  Nothing grabbed my attention so I used my lifeline and asked a Rubyist friend to see what he thought.  He answered [HTTParty](http://github.com/jnunemaker/httparty).  Long story short, I implemented what I thought would work, but it failed when Paul deployed it to the staging server.  Then I saw him modify the form attributes:

{% highlight html %}
<form action="https://remote-server-url" method="post">
{% endhighlight %}

Sigh.  That was too easy.  It bypassed my simple HTTParty call.  Sometimes the answer is not always a third-party gem.  Anyway, we got the form to work, but it looks like the remote server isn't responding so Paul is going to deal with the issue.

## WEBrick Tic Tac Toe

I learned a lot from this Rails app.  From changing the routes, to understanding the Rails conventions, to introducing Bundler and failing because the staging server didn't have Bundler.  I enjoyed learning about Rails.

I worked more on the WEBrick Tic Tac Toe.  The design is looking more like the Limelight version and I've modified the way I introduce the refresh meta tag into the HTML.  I still feel like it's hack and I wish I knew a better way to do this, but since it works, I'm not complaining.  I'm going to try working on it more tonight and continuing reading my books.

## Reading

I spent some time last night reading on The Well Grounded Rubyist and the paper, "Principles and Patterns" by Uncle Bob.  This is the first time I'm understanding one of the SOLID principles, the Liskov Substitution, which states that "derived classes should be subsitutable for their base classes...Derived methods should expect no more and provide no less."  I'm pretty sure I'm violating this principle in my project.  When I read this principle, I thought about polymorphism, and of course there is relationship.  According to this [article](http://www.necessaryandsufficient.net/2008/09/design-guidelines-part3-the-liskov-substitution-principle/), "The Liskov Substitution helps to guarantee inclusion polymorphism, which is a good thing because inclusion polymorphism improves reuse."  I'm going to have to read this article in full when I get home. 
