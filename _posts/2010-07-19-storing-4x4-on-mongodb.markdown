---
layout: post
title: storing 4x4 on mongodb
date: 2010-07-19 21:00:00 -05:00
categories:
  -- software craftsmanship
  -- mongodb
  -- nosql
  -- ruby
---

![TTT Matrix](/images/ttt_matrix.jpg)

I worked on a method to write the best moves for each board state starting from an empty board.  If you think about it, there are 16! possibilities.  As of this writing, there are 28,782,679 documents stored on my local mongodb.  Holy cow.  Li-Hsuan and I did some quick math and it's about 0.02GB now, soon to reach a hypothetical 25GB.  I still need to index the database and test the performance.  I'm hoping it's not going to be slow.

Here is the added code to the NegamaxPlayer class:

{% highlight ruby %}
# ...
require 'mongo'

class NegamaxPlayer < Player

  attr_accessor :best_move

  def initialize(piece)
    super(piece)
    @conn = Mongo::Connection.new
    @db = @conn.db('test')
    @coll = @db.collection('coll')
  end

  # ...

  def store_moves(board, piece, depth, alpha, beta)
    # ...
        if score > alpha
          alpha = score
          best_move = s
          @best_move = s if depth == 1
        end
    # ...
    @coll.insert({"board" => board.to_a, "best_move" => best_move})
    # ...
  end
{% endhighlight %}

I haven't started on the other story which involves creating new Limelight scenes and adding a new theme.  I'm going to work on the themes sketches using Pixelmator and see how I can add it as a prop to my Limelight UI.
