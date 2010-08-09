---
layout: post
title: vows.js, ttt stories
date: 2010-08-08 23:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- limelight
  -- javascript
  -- nodejs
---

*Note:* Apologies for the delay again, but I was a bit under the weather on Saturday.  This post is a combination of last Friday and the weekend.

## Lunch n' Learn - Vows.js

Jim continued the Node.js session, introducing a BDD framework, [vows.js](http://vowjs.org/).  We used the [Prime Factors Kata](http://butunclebob.com/ArticleS.UncleBob.ThePrimeFactorsKata) to learn how to write vows.js tests.  I've heard about the katas from Uncle Bob, but haven't tried them until then.  I really enjoyed going through the kata and it's a really good way to practice TDD.  I'd like to work on the Bowling Kata in the near future.

Our homework assignment for next coming week involves writing tests for the Node.js server we built.  Jim suggested it's best to start over and write tests first to let the design come out of the tests.  I look forward to working on this assignment this week.

## Tic Tac Toe stories

Aside from my loss of Saturday, I worked on my stories today and actually finished the Scoreboard story.  This calls for keeping track of wins/losses/draws for both the console UI and Limelight UI.  This is what it looks like:

Console UI Scoreboard

![TTT Console Storyboard](/images/ttt_console_scoreboard.jpg)

Limelight UI Board with View Scoreboard button

![Limelight UI Board](/images/ttt_board_final_ii.jpg)

Limelight UI Scoreboard

![Limelight UI Scoreboard](/images/ttt_limelight_scoreboard.jpg)

I also managed to fix the transparency issue with some of the images, something Micah pointed out last iteration.  As you can see above, the pieces as well as the messages no longer have a white background.  The trick to solving this was exporting the images as \*.png and not \*.jpg.  Apparently, and I did not know this, but png files support transparency whereas jpg files do not.  Well I guess that's why I notice people using png in GUI development.

There's still a lot to do in this iteration.  I'm still somewhat stuck on the UI design for WEBrick.  I'm not HTML/CSS savvy (yet), so I'm reading up on it, and at the same time figuring out how WEBrick works.  Of course, the Node.js homework helped my understanding of how web servers work.  More on that later.  

## Friday Dinner with 8th Lighters

Colin made a wonderful suggestion to have dinner at a nearby restaurant.  A good number of us went and some invited family members.  It was really great to hang out with the 8th Lighters outside of work.  I really had a great time.  Uncle Bob and his wife made a guest appearance which made the night even better.  Although I didn't get the chance to talk to him, it was a great feeling knowing I'm part of a great team.

