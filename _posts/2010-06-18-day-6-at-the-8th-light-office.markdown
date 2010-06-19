---
layout: post
title: day 6 at the 8th light office
date: 2010-06-18 21:00:00 -05:00
categories:
  -- software craftsmanship
  -- ruby
---

With the help of Micah and Li-Hsuan, I finished the minmax algorithm today.  I still can't believe I finished it, so I'm going to look over the code again this weekend.  The problem to my existing code was the fact that I did not focus on the importance of depth and how it played a crucial role in returning the best move.  If you ever decide to work on this problem, I highly suggest you follow the Negamax version of the minmax algorithm on [Wikipedia](http://en.wikipedia.org/wiki/Minimax):

{% highlight text %}
function integer minimax(node, depth)
    if node is a terminal node or depth == 0:
        return the heuristic value of node
    α = -∞
    for child in node:                       # evaluation is identical for both players 
        α = max(α, -minimax(child, depth-1))
    return α
{% endhighlight %}

This pseudocode was enough to develop the method that will return the best move.  I will post the code later tonight on my GitHub [repo](http://github.com/sl4m/tic_tac_toe_ruby).

Today was my first day grabbing lunch for the 8th Light crew for open door Friday.  I forgot to mention this last Friday, but every Fridays we open our doors to anyone who wants to pair with us, participate in the 8LU (8th Light University) class, and have some deep discussions about everything that is code.  [Eric Smith](http://twitter.com/paytonrules) started a new class for 8LU about developing in OpenGL.  There are homework assignments and we're expected to upload our work on a GitHub repo.  I'm excited to learn about new technologies, programming languages, etc at 8LU.  This is one of many great things that make 8th Light such an awesome environment to be in.

I plan to continue working on the Tic Tac Toe program and plan to read The Well Grounded Rubyist and Metaprogramming Ruby.
