---
layout: post
title: tic tac toe stories
date: 2010-06-29 18:00:00 -05:00
categories:
  -- software craftsmanship
  -- refactoring
---

Today, I demoed my Tic Tac Toe program running the Limelight UI to Micah.  He asked me if I thought it was harder than I initially thought and I said yes.  To be honest, I didn't think the problem was difficult, rather, finding which framework API to call proved to be difficult.  Also I needed to get used to the theatre metaphors.  After the demo, he asked me if I knew the four criterias of a [story](http://www.agilemodeling.com/artifacts/userStory.htm).  Having zero experience working in an Agile environment, I said no.  Last year, I spent some time reading about Agile, but unfortunately did not have an environment to practice in.

The four criterias of a story are that it must:

* deliver business value to the customer
* be estimable and establish velocity
* be testable*
* "fit" in a half iteration's worth of time

\*certain exceptions include, but not limited, to UI design related stories

You might be wondering about the last criteria.  What does "fit" mean?  How long is an iteration?  Here at 8th Light, each iteration is one week long and a craftsman should commit to completing ten points per iteration.  Story points are a way to estimate how long it will take the developer to complete the story.  So to meet our criteria, a story should be anywhere from 1-5 points.

Micah played the role of a customer, I played the role of a developer and he created story cards for each of the stories.  There were ten story cards on the table and he asked me to estimate each story in points.  Most of the stories I was able to estimate, but the others I had a hard time estimating because I didn't understand the root of the problem.  I needed time to explore the code, docs, etc. to be able to provide estimates.  There's actually a name for this kind of exploring.  It's called spiking.  While spiking is not often used, when used, you're suppose to write the word "spike" next to the story points.  I ended up doing that and completed the estimations.

Micah ("customer") then picked out the stories for the first iteration.  Customers usually pick out the stories, but developers are welcome to make suggestions.  He picked seven story cards total and I'm suppose to have them completed by next Tuesday.  This is quite exciting and intimidating at the same time.  Some of the stories he picked, I think I can "fix" pretty quickly, but the ones that require spiking, I'm not too sure about.

Micah gave me the choice of using [GitHub Issue Tracker](http://github.com/blog/411-github-issue-tracker), [Pivotal Tracker](http://www.pivotaltracker.com/), or [AgileZen](http://agilezen.com/) to track my stories.  Luckily, I have some experience with all three.  He preferred using AgileZen, so we created a project.  I entered the ten stories and have already completed a story.  I look forward to getting a lot of work done this week.  I'll be pushing my story code in a different [branch](http://github.com/sl4m/tic_tac_toe_ruby/tree/ll-refactoring)

![AgileZen TTT](/images/agilezen_ttt.png)
