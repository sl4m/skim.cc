---
layout: post
title: rails and reading code 
date: 2010-08-17 23:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- rails
  -- reading
---

Today Matt and I met at the Libertyville office to pair on the Rails project.  Last night, while on the train, I tried working through sample code that would send a POST request automatically using HTTParty, but for some reason I could not get it to work.  We asked Micah for some help and within minutes, had a working solution for the project.  Mentor help availability cannot be taken for granted.  He basically ran a simple test using curl, then switched over to Ruby's net/http standard library to find a solution.  I think I'm finally going to give HTTParty a rest and use the net/http solution.  Here's sample code with the help of this [article](http://snippets.dzone.com/posts/show/788):

{% highlight ruby %}
require 'net/http'
require 'net/https'

Class Sample

  def post
    http = Net:HTTP.new('http://url', 443)
    http.use_ssl = true
    response, data = http.post('path/to/request', 'name1:value1&name2=value2')
    puts data
  end
end
{% endhighlight %}

Now that we spiked the code, we cleaned out the project and began writing specs against a class that handles the post requests.  With the help of the 8th Lighters in the office, we were able to ask questions and get some guidance on how to implement the feature into the project.  Matt and I will be working on this throughout the week and I hope we can finished it sooner than expected.

## Reading Other People's Code

I'm trying to do a lot of reading at home to learn more about Rails conventions, Ruby, RSpec, and web development in general.  I just picked up Ruby Design Patterns to understand ways to design code (don't worry I still plan to read the other books).  I'm also planning to take some time to read other people's code.  A [tweet](http://twitter.com/redsquirrel/status/21400168392) from Dave Hoover today sparked an idea about learning from other people's code.  Last week, I read some of the source for the WEBrick library and while reading code in [Specjour](http://github.com/sandro/specjour), noticed some similarities in design and structure.  Things like wrapping all classes in the same module to create a shared namespace, creating a main file that lives on the root outside of lib that runs all the requires, autoloads, versioning, logging features - reading the code sparked ideas in my head about how I can refactor my Tic Tac Toe game engine and turn it into a library that other UIs can easily implement.  

Hopefully, I'm not overwhelming myself by doing too much all at once.  This is exciting time for me to learn all kinds of things to help become a better developer.  If only I had all the time in the world, I could maybe finish reading the things I want to read...when [squids fly](http://www.scientificamerican.com/article.cfm?id=can-squid-fly)...oh wait.
