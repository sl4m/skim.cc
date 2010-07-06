---
layout: post
title: tic tac toe on a holiday
date: 2010-07-06 11:45:00 -05:00
categories:
  -- software craftsmanship
  -- refactoring
---

*Note:* In my previous posts, I called the algorithm I used [Minmax](http://en.wikipedia.org/wiki/Minimax), where in fact it's really [Negamax](http://en.wikipedia.org/wiki/Negamax).  Going forward with this post, I will call it Negamax.

I worked a bit on the Tic Tac Toe stories, but mostly distracted from the nice, holiday weekend.  Unfortunately, The Sight Below canceled so I did not go to his show.  I guess there's always a next time.  

I probably shouldn't have worked on a story that was not under the Working phase, but this is what I ended up doing.  I have a bad habit of scratching my own itch and story #11, "MinMax Player takes too long to move" was the itch.  I was trying to implement the alpha-beta pruning for the Negamax algorithm in hopes that it will resolve the lag present in the game.  I looked at three different pseudocodes I found on the internet:

[MinMax with Alpha-Beta pruning](http://www.ocf.berkeley.edu/~yosenl/extras/alphabeta/alphabeta.html) (not Negamax)

{% highlight text %}
alpha-beta(player,board,alpha,beta)
    if(game over in current board position)
        return winner

    children = all legal moves for player from this board
    if(max's turn)
        for each child
            score = alpha-beta(other player,child,alpha,beta)
            if score > alpha then alpha = score (we have found a better best move)
            if alpha >= beta then return alpha (cut off)
        return alpha (this is our best move)
    else (min's turn)
        for each child
            score = alpha-beta(other player,child,alpha,beta)
            if score < beta then beta = score (opponent has found a better worse move)
            if alpha >= beta then return beta (cut off)
        return beta (this is the opponent's best move)
{% endhighlight %}

[Negamax with Alpha-Beta pruning](http://en.wikipedia.org/wiki/Negamax) (with color argument)

{% highlight text %}
function negamax(node, depth, α, β, color)
    if node is a terminal node or depth = 0
        return color * the heuristic value of node
    else
        foreach child of node
            α := max(α, -negamax(child, depth-1, -β, -α, -color))
            {the following if statement constitutes alpha-beta pruning}
            if α≥β
                return α
        return α
{% endhighlight %}

[Negamax with Alpha-Beta pruning](http://en.wikipedia.org/wiki/Alpha-beta_pruning) (without the color argument)

{% highlight text %}
function alphabeta(node, depth, α, β)         
    (* β represents previous player best choice - doesn't want it if α would worsen it *)
    if  depth = 0 or node is a terminal node
        return the heuristic value of node
    for each child of node
        α := max(α, -alphabeta(child, depth-1, -β, -α))     
        (* use symmetry, -β becomes subsequently pruned α *)
        if β≤α
            break                             (* Beta cut-off *)
    return α
{% endhighlight %}

When I first spiked and tried implementing the code, I used the first pseudocode from Yosen Lin's article.  Unfortunately, it was not using Negamax, so I couldn't figure out how to implement alpha-beta pruning to my Negamax code.  I then looked at the second pseudocode, but I didn't quite understand the color argument.  The way I implemented Negamax, I did not need color to switch between pieces (aka colors).  When I looked at the last pseudocode, I caught something I overlooked in the second pseudocode - the recursive call inside the function had the alpha and beta values not only switching signs, but were swapped as well.  When I fixed the code and also make it look more like the last pseudocode, it started working.  And boy was it significantly faster than the original Negamax code.  Here is the code:

{% highlight ruby %}
  def get_alpha_beta_move(board, piece, depth, alpha, beta)
    if board.game_over?
      return evaluate_score(board, piece, depth)
    else
      opponent = get_opponent(piece)
      empty_squares = board.get_empty_squares
      empty_squares.each do |s|
        temp_board = Board.new(board.to_a)
        temp_board.move(s, piece)
        score = -get_alpha_beta_move(temp_board, opponent, depth + 1, -beta, -alpha)
        if score > alpha
          alpha = score
          @best_move = s if depth == 1
        end
        break if alpha >= beta
      end
      return alpha
    end
  end
{% endhighlight %}

If you take a look, the key line is where it breaks the loop when alpha is greater or equal to beta.  This is where it prunes branches that give no value to the MinMax player.  To test the performance differences between Negamax code and Negamax with alpha-beta pruning code, I tested how long it took the MinMax player to make its first move in ten separate games.

<table>
<thead>
<tr>
  <th align="left">Negamax</th>
  <th align="right">Negamax with Alpha-Beta pruning</th>
</tr>
</thead>
<tbody>
<tr>
  <td align="left">7.014</td>
  <td align="right">0.836</td>
</tr>
<tr>
  <td align="left">6.75</td>
  <td align="right">0.53</td>
</tr>
<tr>
  <td align="left">6.324</td>
  <td align="right">0.469</td>
</tr>
<tr>
  <td align="left">5.576</td>
  <td align="right">0.45</td>
</tr>
<tr>
  <td align="left">5.893</td>
  <td align="right">0.368</td>
</tr>
<tr>
  <td align="left">5.392</td>
  <td align="right">0.312</td>
</tr>
<tr>
  <td align="left">5.409</td>
  <td align="right">0.311</td>
</tr>
<tr>
  <td align="left">5.508</td>
  <td align="right">0.325</td>
</tr>
<tr>
  <td align="left">5.633</td>
  <td align="right">0.258</td>
</tr>
<tr>
  <td align="left">5.569</td>
  <td align="right">0.3</td>
</tr>
</tbody>
</table>

As you can see, the pruning significantly helps the first move.  The median for Negamax only code was *5.6045* while Negamax with alpha beta pruning was *0.3465*.  The mean for Negamax only was *5.9068* and the Negamax alpha beta pruning was *0.4159*.  You might also notice the times for both algorithms improved after each iteration.  I could be wrong, but I think it has something to do with the JIT-compiler in JRuby.  Yes, these tests were run using JRuby 1.5.1 (1.8.7-p249).

Well, I hope you learned something from this.  I sure did.  Negamax with alpha beta pruning is clearly the winner.  There are other, [modern algorithms](http://en.wikipedia.org/wiki/Alpha-beta_pruning#Other_algorithms) which are even faster, but I think it might be overkill for a simple game like Tic Tac Toe.

I shot an email to Micah (customer) last night and he prioritized the backlog stories so I can work on them in this new iteration.  More on that in another post...
