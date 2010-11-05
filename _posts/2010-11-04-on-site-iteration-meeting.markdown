---
layout: post
title: on-site iteration meeting
date: 2010-11-04 23:59:00 -05:00
categories:
  -- client
  -- rails
  -- javascript
---

I drove down to the client's office today to sit in for the weekly iteration meeting with Jim and the Erics.  The meeting consisted of the stories that were due for this iteration and what's to come for the next iteration.  Of course, they did not know what was involved in the next iteration until the stories were estimated right then and there.  So they had to estimate them...using their hands.  I like this approach.  On the count of three, each person throws out a number.  Of course, not everyone will estimate the same number of points, so there's a short discussion to convince one another how it's this many points or that many points.  Usually, in a situation where there's three developers estimating stories, the favor is on the two that has nearly identical estimates.  At least, that was the pattern I noticed today.  New stories, bugs, and production support were all part of the new iteration.  They also talked about automating deployments, new development features, and specific bugs.

After the meeting, followed by lunch, Jim and I sat down and started working on a couple of customer\-facing bugs that were JavaScript related.  We were able to identify the problem right away and fix them.  Something I'm aware of as a tester, but have not experienced as a developer is the inevitable differences between each browser's ability to render pages.  Not all browsers were created equal and each of them have their own standard for what's regarded as an error.  One particular bug was only noticeable in Internet Explorer 7, while WebKit based browsers did not show the error at all, not even IE8.  This was a rare moment where I sided with IE7's feature to display the error because it was not so great JavaScript code.  I won't go into details, but it shouldn't have worked and IE7 barked up the right tree while others did not.  Of course, the end user doesn't care for errors, but as developers, it's nice to get some visual feedback during testing to avoid end users from seeing them.

## Next stop on the tour

This concludes my working with Jim and the Erics.  I enjoyed working with them and learning about the projects they work on as well as their technical skills which I'd like to pick their brains another day.  Time was well spent on the deployment, staging, IT side which I'm still not too familiar with and would like to learn more.  Also the projects are fairly large and I'd like to learn more about them so I can contribute to the iteration.  Anyway, I had fun and look forward to working on the project again.

Starting tomorrow, I will be working with Paul at the Chicago office and will be working with him on a Rails project which I'm familiar with since the last time I worked on it.  It should be fun working on the project again and look forward to the stories.
