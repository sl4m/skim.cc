---
layout: post
title: end of iteration recap and apprenticeship challenge
date: 2010-10-05 17:00:00 -05:00
categories:
  -- software craftsmanship
  -- yak shaving
  -- java
  -- ruby
  -- stories
  -- tic tac toe
---

## End of Iteration 11

I am happy to say I've finished all stories for Iteration \#11 and managed to catch and finish the Tic Tac Toe project in Rails 3.  Micah and I had our meeting today to talk about each story and my first apprenticeship challenge.

#### Fixed bug in statemachine gem

Earlier in Iteration \#11, I fixed a small bug in the statemachine gem and submitted a pull request.  Micah applied the fix and pushed out a new version.  I demoed the Java generator and it correctly generated the states.

#### Limelight Styles Parser

This zero point story took a bit more time than I initially thought.  While most of the features were implemented from Iteration \#10, it still needed to support comments.  As described in my earlier posts, when the parser finds a '\#' (and not in a string), it transitions into a purgatory state where all characters are discarded.  It waits until it sees new line to get back to the previous state from purgatory state and resume parsing the file.  When I picked up Justin from the train station, this morning and told him about the solution, he helped me discover a problem I had.  In order to determine that the '\#' was not in a string, I stored the previous character.  This worked great to resolve style attributes that have '\#' in them (e.g., #FFFFFF), but does not fare well when the '\#' is not first character of a string.  Fortunately, Micah let it slide since it's not a common situation you'll find in a styles.rb file.

#### FitNesse/SliM

This also took longer than I expected.  I needed to figure out the DSL that is SliM.  Fortunately, from the SliM Overview video and some trial and error and I was able to get through and create tests.  Micah pointed out during the demo, that the acceptance tests should be easy to understand and anyone should be able to know what it's testing.  I had stored the expected output in files, but I could have easily stored them in the SliM table.  Using the literal text markup, I could have stored multi-line text.

#### Tic Tac Toe in Java

This story was easier than I thought and using my Ruby version as reference, I was able to easily write the game test first.  I explained to Micah about the mocks I created for both stdin and stdout and ran a quick demo via console.

#### Tic Tac Toe in Rails 3

Finally, Tic Tac Toe in Rails 3 was a nice story to work on.  I skimmed (no pun intended) through the Edge Rails Guide for Rails 3 and learned more about Rails 3, much more than I did the first time around.  I ended up eliminating the game engine duplication as described in this [post](http://skim.cc/2010/10/04/return-of-tic-tac-toe-rails-3), learned how to test controllers, understood more about models, and learned more about the new RSpec (e.g., executing specs via bundler).  I demoed the game and it worked like my WEBrick implementation.

## Apprenticeship Challenge

My apprenticeship challenge is to write an HTTP server that will serve default MIME types as well as parse GET request params.  More on that this week.
