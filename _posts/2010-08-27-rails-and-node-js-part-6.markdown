---
layout: post
title: rails and node.js - part 6
date: 2010-08-27 17:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
  -- patterns
  -- nodejs
  -- websocket
---

We finished the Rake task.  With the help of [Eric Smith](http://twitter.com/paytonrules), Matt and I were able to get past a roadblock from yesterday and do a bit of refactoring I couldn't quite figure out.  A little Google search yielded a nice little tutorial on [Rake](http://jasonseifer.com/2010/04/06/rake-tutorial).  To load the Rails environment in Rake, we basically needed to put this in our code:

{% highlight ruby %}
namespace :api_example do
  desc "Update user records by calling API Example"
  task :update_users => [:environment] do
    # task code here
  end
end
{% endhighlight %}

The \[:environment\] piece loads up the Rails environment.  Then in the console, we run the rake task like this:

{% highlight text %}
[some_branch][~/local/git/some_repo] rake api_example:update_users
{% endhighlight %}

We demoed the work we've done in the past couple of weeks to Paul and he seemed impressed with it.  It will be demoed to the customer next Monday, but before then, Paul will walk us through the deployment process.  I'm glad to have worked with Matt and Paul on this Rails project.  I've definitely learned a lot.  I feel like my RSpec and Ruby skills have improved.  I've gained more experience on pair programming and learning more about the backend - MySQL, ssh, running rake tasks, learning about environment variables (e.g., RAILS\_ENV), script/commands, etc.

## Node.js Knockout

Node.js Knockout starts today and it's pretty exciting, at the same time, nerve wrecking.  I would love for us to complete the project we want to work on, so I hope to contribute as much as I can to get this working.  I know we will learn a lot of things out of this challenge.  This will be an exciting experience working with three other people I have not worked before and plus learning how they develop and [be the worst](http://apprenticeship-patterns.labs.oreilly.com/ch04.html#be_the_worst) (but try to contribute).  I will give details about the weekend experience...after the weekend.
