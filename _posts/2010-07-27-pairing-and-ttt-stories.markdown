---
layout: post
title: pairing and ttt stories
date: 2010-07-27 22:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- stories
  -- pairing
---

Paul needed a pair today so he asked me and I gladly accepted.  The last time I paired with Paul when I was in the 8th Light office for the first time before the apprenticeship offer.  It was great to pairing with him because I get more exposure to the framework I really want to know inside out - Rails.  For a couple of hours, we worked on a story and created acceptance tests using Cucumber and generated a controller, model, view with its respective specs.  It was great getting some exposure to the variety of tools used in Rails projects.  I had the opportunity to ask Paul many questions and he was kind enough to answer them all and elaborately.

![TTT New Look](/images/ttt_new_look.jpg)

After lunch, I went back to working on my UI stories.  I had finally fixed those nasty failures in the specs after moving Board Type, Player O, Player X, Start Game, Exit to the new Options scene.  There was a bit of trouble when I was fixing a method that removes the existing board on a new game.  *scene.children* was not responding to the way I wanted it to when deleting child props.  The code example below does not work:

{% highlight ruby %}
scene.children.each do |p|
  scene.remove(p) if p.name == "something"
end
{% endhighlight %}

What ends up happening is when the first child is deleted, the children collection shifts up one, so it skips deleting the second one.  During my debugging session, I saw it deleted every other prop.  I talked to Eric Meyer about it and he seemed to have experienced the issue himself.  He showed me a workaround solution - basically run through the children collection to find the props you want to delete and store them into an array.  Then loop through the new array to delete them.

{% highlight ruby %}
children_to_remove = []
scene.children.each do |p|
  children_to_remove << p if p.name == "something"
end

children_to_remove.each do |p|
  scene.remove(p)
end
{% endhighlight %}

My specs now pass and the game runs as great as it did before.  I think I might miss my full 10 points for this iteration which I'm not too happy about.  As you can see from the image above, the layout looks completely different, but it's not quite there to be delivered to the customer.  I still need to add the Try Again message and add the Quit button to the Board scene.  Also another story calls for keeping track of the scores.  I'm going to push through the first half of tomorrow to get a lot of it done (hopefully).  Iteration #4 ends tomorrow afternoon.
