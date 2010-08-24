---
layout: post
title: rails and refactoring
date: 2010-08-23 23:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
  -- refactoring
  -- patterns
---

> "Read, Learn!  Never stop learning.  Learn many languages.  Learn many disciplines.  Practice TDD and never let it go.  When you write code, write the best code you can.  Never succumb to the temptation to rush.  The only way to go fast, is to go well!" - @unclebobmartin, [interview](http://www.azullo.com/blog/think-agile/interview-with-robert-c-martin-co-author-of-the-agile-manifesto/)

Matt and I continued working on the Rails project adding another feature to send and receive post form data.  Both features share some methods, so I thought now was a good time to experiment with the "pattern" I've been [seeing](http://github.com/sandro/specjour) in ruby gem source code.  I took our class that contained the first feature, moved it under a parent module and abstracted shared methods into a child module of the same parent module.  By creating the parent module, I have created a namespace to prevent any name conflicts and such.  The new feature is also part of the same namespace in its own class and includes the child module to call shared methods.  I showed Matt and Paul of the new change, and they seem to be okay with it.  We made sure our existing tests passed and moved on to the new feature.  I think the experiment was a success. 

The feature called creating new column to an existing table.  Luckily with Rails conventions, it's a rather simple process:

{% highlight text %}
cript/generate migration AddNewColumnToTable new_column:string
      exists  db/migrate
      create  db/migrate/20100823165501_add_new_column_to_table.rb
{% endhighlight %}

AddNewColumnToTable is actually broken down conventionally: Add NewColumn To Table.  After, we ran *rake db:migrate* for both development and test RAILS\_ENV.  A solid 15 minutes or so, we were stuck at a problem where the new column was not accessible via accessor.  We found out later we needed to load the database schema for the test environment (I'm taking a guess - it's because the test database is always empty, so the migration rolled back):

{% highlight text %}
[some_branch][~/local/git/some_repo] rake db:schema:load RAILS_ENV=test
{% endhighlight %}

We do hit some roadblocks every now and then due to our limited knowledge of Rails and experience, but I'm actually quite surprised at the rate we're progressing.  We probably owe it to Rails' conventions - once you get the hang of it, it's actually really easy to get around.  In an effort to move things along, I'm going to pick up some Rails knowledge on the side.  Luckily, I have a couple of Rails books I can use as resources.

## Refactoring

I noticed the last time I talked about refactoring from Martin Fowler's book was probably back in late June.  I shall pick up where I left off here with a couple of refactorings.  Last night, I remembered Doug's favorite refactoring pattern was "Replace Conditional with Polymorphism."  I read about it, and it's a refactoring pattern similar to one of the SOLID principles: Dependency Inversion Principle.  It talks about avoiding writing explicit conditionals and to look for switch or if/else statements that check type.  These are places where this refactoring pattern will become handy.

I use the move method refactoring a lot and it's nice to know the name of what I'm using.  When classes have too much behavior or are collaborating too much and are too highly coupled, move method should be used.
