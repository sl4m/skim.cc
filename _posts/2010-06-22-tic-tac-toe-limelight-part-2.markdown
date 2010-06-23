---
layout: post
title: tic tac toe on limelight - part 2
date: 2010-06-21 22:30:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- limelight
---

Today I took my newly created "production" and integrated it into my Tic Tac Toe project on [GitHub](http://github.com/sl4m/tic_tac_toe_ruby).  I followed the [Hangman](http://github.com/slagyr/hangman) production example which provided a lot of answers to my questions and gave me a better understanding of what I need to do to my project to integrate Limelight's UI.

The first thing I did after integrating the production was to change the way the current stdio/stdout UI was integrated with the TicTacToe class.  I renamed the UI class to StdUI to make it less generic and now I have to figure out how to integrate my existing code with the new production.

One thing I notice is the design changes I'll need to make to the existing code to fit the new UI.  Before, with the stdin/stdout UI, TicTacToe class acted like a production.  It made sure everything wired together properly to create a game environment.  However, the production plays that role with the new UI.  Limelight will be responsible to wire everything together to create the game environment.  I'll need to dig into more of the Hangman source code, but that is basically the gist I'm getting.

Later in the day, [Li-Hsuan](http://twitter.com/li_hsuan) and I took [Anders](http://twitter.com/unders) from [eLabs](http://elabs.se/) to a local Korean BBQ restaurant.  I haven't had a chance to eat at a Korean restaurant since I arrived, but I must say I was impressed.  If I need my Korean food fix, I know where to go now.  As you may know, 8th Light and eLabs are currently in a craftsmanship swap.  This is where one of our 8th Lighters goes out to eLabs to learn about how eLabs craft code, engage with customers, etc. and vice versa.  You can read about their experiences [here](http://blog.8thlight.com/articles/2010/6/21/international-craftsman-swap-day-1) and [here](http://elabs.se/blog/11-first-impressions-of-my-craftsmanship-swap-with-8th-light).  I hope to one day participate in the swap, whether it be domestic or international.
