---
layout: post
title: client work on a windy day
date: 2010-10-28 09:30:00 -05:00
categories:
  -- client
  -- ruby
  -- eventmachine
---

We continued working on the EventMachine library for our client, adding more features Doug needs to make the implementation work.  One big feature we nearly finished yesterday (just needs integration testing) is storing more than one callback on both the server and client side.  Before, both sides were only storing a single callback.  Doug ran into a problem where the second callback overwrote the first one because the second remote call finished before the first.  Now we're storing the callbacks in a hash with a unique key which is passed as part of the message that gets sent through the remote call process.  This broke a lot of tests and we spent more time fixing the tests and making them pass than writing actual code.  I'm wondering if our design has smells which makes it difficult to change the code and the ever changing requirements.  I think we should look at the design as a whole and see there are any SOLID principle violations, and make changes necessary.

Our next task is to work on filtering out "insecure" methods on remote calls.  The library currently allows both sides to make remote method calls (e.g., call the remote API's methods).  Since all Ruby objects come with a set of default methods, we don't want the client to call methods on the server that could potentially do harm (e.g., instance\_eval, instance\_variable\_set, methods).
