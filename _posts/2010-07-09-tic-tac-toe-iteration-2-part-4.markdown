---
layout: post
title: tic tac toe - iteration 2 - part 4
date: 2010-07-09 18:30:00 -05:00
categories:
  -- software craftsmanship
  -- refactoring
---

Eric Smith continued Lunch n' Learn on OpenGL covering topics on 2D textures and different types of lighting.  Before that, Eric demoed everyone's homework and mine looked nothing like the other 8th Lighters who put a lot more effort into the code.  I had trouble figuring out what each function call meant and where to look for examples, not to mention trying to work the problem at the last minute.  Since we don't have new homework for next week, I plan to continue working on what I have to make it more 3D and include some lighting elements.

![OpenGL Demo](/images/opengl_example.jpg)

I worked a bit on Story #14, "Optional 4x4 board", by adding features to the StdUI class first.  I wanted to get the 4x4 board methods into the proper classes first without worrying about Limelight UI stuff.  Here's a list of items I came up with in order for the 4x4 board to work:

* ask the user for board type (3x3 or 4x4)
* get board type from STDIN
* create board with specific size
* display board correctly
* add board winning patterns
* add 4x4 board winning/blocking patterns CpuPlayer class

Since CpuPlayer class is using rule-based logic to win/defend, I need to add the pattern set for a 4x4 board.  EasyCpuPlayer uses pure randomization to move its piece so nothing changes there.  NegamaxPlayer uses the Negamax algorithm which is not affected by the board size either.

I look forward to finishing up this story and work on the mock-up story.  Have a great weekend!
