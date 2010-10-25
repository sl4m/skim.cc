---
layout: post
title: client work, ppp
date: 2010-10-24 23:30:00 -05:00
categories:
  -- client
  -- java
  -- ppp
---

## Client Work

On Friday, Li\-Hsuan and I continued working on the story we started Thursday and completed it by the end of the day.  We showed Doug our work and he was happy with it and we checked it in.  During the day, he asked us to create a local gem for one of his libraries.  I took over the task and created the gem.  There's a nice gem out there called [jeweler](http://github.com/technicalpickles/jeweler) that pretty much does all the work for you.  I first created a blank project using jeweler:

{% highlight text %}
[~/local/git] jeweler test-gem
{% endhighlight %}

I only did this so I can grab the Rakefile it auto-generates.  The Rakefile is pretty much all you need.  I opened up the Rakefile and modified the values in there:

{% highlight ruby %}
Jeweler::Tasks.new do |gem|
  gem.name = "test-gem"
  gem.summary = %Q{Some summary}
  gem.description = %Q{Some description}
  gem.email = "skim@email.com"
  gem.homepage = "http://github.com/sl4m/test-gem"
  gem.authors = ["skim"]
  gem.add_development_dependency "rspec", ">= 1.3.0"
  gem.add_dependency "eventmachine", ">= 0.12.10"
  # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
end
{% endhighlight %}

Then I ran the following command:

{% highlight text %}
[~/local/git/test-gem] rake install
{% endhighlight %}

This will build the gem and install it.  You can also use *rake build* to build the gem.  *rake -T* will show you other rake tasks you can execute.

After all of that, Li\-Hsuan and I were assigned another task: to work on an [EventMachine](http://github.com/eventmachine/eventmachine) related problem.  I've not worked on EventMachine, but I heard it's similar to Node.js.  We weren't able to complete the task in time, but I took some time over the weekend to read up on EventMachine.

## PPP Book

I read a bit more from the PPP book.  It went through the seven design smells and the SOLID principles, both of which I [blogged](http://skim.cc/2010/08/10/principles-and-patterns) [about](http://skim.cc/2010/08/13/principles-and-patterns-part-2).  I quickly read through them again and found some gems.

#### Requirements Changes Are Not The Fault of Customer

When I worked as a software tester, I helped develop some tools for our team and remember wanting the entire design up front (BDUF).  I also remember having the same conversation as the book, where I talked to the manager and told him that the requirements can't change.  Of course they can!  This should be expected when working in software.  Customers will make changes.  The design should be resilient to requirement changes, able to meet them without showing signs of design smells.

#### Anticipating Change

While there's an advantage to add protection to your design to requirement changes, if you don't expect change in a particular area, adding protection might be wasted effort and make the design more complex.  As long as the design makes it easy to add protection, then it's best to add it later when the change calls for it.
