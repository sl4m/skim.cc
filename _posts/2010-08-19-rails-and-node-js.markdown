---
layout: post
title: rails and node.js
date: 2010-08-19 22:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
  -- javascript
  -- nodejs
---

Today, Matt and I briefly worked on the Rails project.  We added a configuration option that allows the feature we implemented to be turned on and off.  I think Paul mainly wanted this for the demo tomorrow.  I committed the changes, but didn't push it to the GitHub repo.  For some reason, I had trouble creating a remote branch, so I did some reading on the net.  I'm not sure why I didn't have problems before when creating branches on my Tic Tac Toe project, but I had to follow a different path to create a remote on a GitHub repo I do not own.

I updated [my post](http://skim.la/2010/06/28/git-branching-and-merging) on git branching and merging.  Basically, I needed to execute this command:

{% highlight text %}
git push origin origin:refs/heads/new\_branch
{% endhighlight %}

Once I created the new remote branch, I was able to create a local branch, have it tracked with the remote branch, and check it out, all in a one-liner command:

{% highlight text %}
git checkout --track -b new\_branch origin/new\_branch
{% endhighlight %}

Bingo!  New branch is tracked, and I'm able to push and pull without stating the additional parameters: repository and refspec.

While we waited for the next assignment, I read the entire page on [vows.js](http://vowjs.org/) to learn what it's about and to help create tests for [my node.js example](http://skim.cc/2010/08/06/nodejs/).  The examples on vows.js weren't that particularly helpful when it came to testing out the node.js server and the methods that handle GET/POST requests.  Maybe it assumes you already know how to test them?  If so, I need to do some catching up because I'm having a little trouble.  I also found out it doesn't have any mocking features and some parts feel a bit unintuitive.  When I sat down with Colin late in the afternoon, we ran into a problem where the topic wouldn't accept a function directly.  I think vows.js attempts to invoke the function, which Colin didn't want.  So by wrapping an anonymous function around the original function and have it returned, Colin was able to the use the original function.  It felt like a needless step, but I guess that's just the way it works.

Node.js Knockout is next week, and I don't feel fully prepared.  I should really know my Node.js if I want to make contributions to our project.  I will be focusing on Node.js everyday to brush up on my JavaScript/web skills.
