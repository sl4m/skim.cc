---
layout: post
title: ui story complete
date: 2010-07-29 21:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
  -- stories
  -- limelight
---

The UI story is finally complete.  Unfortunately, I had underestimated the story as one point; it actually took three points.  I sent an email to the customer asking if he likes the new UI layout and mentioned the story took longer than expected, but I'm going to hold off on potentially warning the customer that not all stories will be completed for Iteration 5.  Even I'm slightly behind, I'd like to wait until after the weekend.  I'll hopefully be able to catch up then.

Here is the new Options scene:

![TTT Options Final](/images/ttt_options_final.jpg)

Here is the new Board scene:

![TTT Board Final](/images/ttt_board_final.jpg)

Most of the props you see now are image based using a font called Party LET on the Mac.  Since the Windows platform does not support this font, I decided to use image based props.  Personally, I think the new layout looks more playable, at the least, more pleasing to the eye than the awful gradient look.  Hopefully the customer will enjoy it much more than the work involved.  Conveniently, I packed the program as an \*.llp file and it's available in the [Downloads](http://github.com/sl4m/tic_tac_toe_ruby/downloads) section of my GitHub repo.  Unfortunately, the mongoDB needs to re-memoized since it was too big to store on the repo (~1.04GB).  You should be able to easily play the 3x3.

The next story I'm going to work on involves creating a configuration file that enables/disables the 4x4 board.  Until then...
