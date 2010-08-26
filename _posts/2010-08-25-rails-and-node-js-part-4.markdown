---
layout: post
title: rails and node.js - part 4
date: 2010-08-25 23:59:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
  -- patterns
  -- nodejs
  -- websocket
---

Another feature has been completed on the Rails project.  Fortunately, today we were given the new URLs for the APIs that we needed to implement.  By testing it out in an IRB session, we were able to make sure the APIs worked (as intended) and see what we needed to do to create the code.  Yesterday, I talked about using DelayedJob or Resque to handle our background jobs, but after talking to Colin in the morning, we both agreed those libraries might be overkill for what we need.  Matt and I briefly spoke with Paul and I basically told him we would use simple cron jobs to handle the background jobs using [whenever](http://github.com/javan/whenever).  Whenever allows you to create cron jobs with clean Ruby syntax.

So as said above, we finished one API and began working on another to pull customer data.  This API will be the most time-consuming to implement since we need to update the User table and create a hash map of new fields to old.  We also migrated a bunch of new fields to the table that need to be created in order for this API to work properly.  A neat little tip from Colin when creating mass fields is to just create one and edit the migration file to add the others:

{% highlight text %}
[some_branch][~/local/git/some_repo] script/generate migration AddNewFieldToTable new_field:string
      exists  db/migrate
      create  db/migrate/20100823165501_add_new_field_to_table.rb
{% endhighlight %}

Open migrate/20100823165501\_add\_new\_field\_to\_table.rb to add other fields, rename the class, and rename the file name to make it more meaningful about what you're doing.  Then *rake db:migrate*.

These new API calls require credentials, so instead of storing the credentials in the class, we stored them in a yaml file and created a layout similar to the database.yml.  Of course, as with any credentials, it's best not to commit the yaml file to the git repository, so another great tip from Colin was to create another folder under config (e.g., local), store the yaml file there, and add that folder to .gitignore.  This way, you can still use the credentials for development/test, but it won't be checked in to the git repository.  I noticed we were also storing the URLs to the APIs in the classes, so I moved them appropriately in the new yaml file.

I'm always learning something in this Rails project and it's a great testament how important it is to have a [breakable toy](http://apprenticeship-patterns.labs.oreilly.com/ch05.html#breakable_toys) when learning new languages/technologies.  I look forward to learning as much as I can in this project.

## Node.js Peepcode Screencast

I watched the [Node.js Peepcode screencast](http://peepcode.com/products/nodejs-i) and enjoyed learning more about Node.js.  With the recent projects I've been working on (e.g., TicTacToe on WEBrick, Node.js, Rails), I'm learning a lot about web development, GET/POST, request/response, and more.  I think I'm comfortable with them now and I understood most of everything from the screencast.  Callbacks are still strange little features to me, but it makes sense how they create asynchronicity.  Unfortunately, the demo Geoffrey used in the screencast did not work for me.  I think the external service is down.  As much as I'd like to agree how Node.js provides clean errors to understand what you did wrong, it sometimes spits out errors that will have you run around for a bit.  I guess as I get more comfortable using the library, I will have a better feel for what each error means.  

Rails offers a development, test, and production environment automatically and the ability to easily switch between them.  Sadly, Node.js does not.  But fortunately, Geoffrey provided a nice server script that you run that watches for any changes in the project and restarts the server for you.  Also, he structured the project layout very similar to Rails to modularize the code for readabiliy and accessibility.  I think I will use this setup for the Node.js Knockout.  That being said, I recommend this screencast as it does contain a lot of good information to get started on Node.js (my unbias review).
