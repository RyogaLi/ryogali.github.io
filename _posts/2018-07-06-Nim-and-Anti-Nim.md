---
layout: post
title:  "Nim and Anti-Nim"
tags: [Fun, Algorithms]
---

> **Nim** is a mathematical game of strategy 
in which two players take turns removing 
objects from distinct heaps. On each turn, 
a player must remove at least one object, 
and may remove any number of objects provided 
they all come from the same heap. The goal of 
the game is to be the player who removes the 
last object.

(From [wiki](https://en.wikipedia.org/wiki/Nim))

---

#### Game play: ####

There are three piles, or nim-heaps, of stones. Players 1 and 2 alternate
taking off any number of stones from a pile until there are no stones left.
There are two possible versions of this game and two corresponding winning
strategies that we will see. Note that these definitions extend beyond the
game of Nim and can be used to talk about impartial games in general.

* **Normal Play** The player to take the last stone (or in general to make
the last move in a game) wins. This is called normal play since most
impartial games are played this way, although Nim usually is not.

* **Misere Play (Anti-Nim)** The player that is forced to take the last stone loses.

---

####Types of impartial game positions####

* A game is in a **P-position** if it secures a win for the Previous player
(the one who just moved).

* A game is in a **N-position** if it secures a win for the Next player.

Then we can think about this problem as **backwards induction**. The **terminal position**
of this game is always $$(0, 0, 0)$$ and we can label this as the **P-position**
And that any position $$(0, 0, n)$$ is an **N position**.

Lets say we have three heaps: $$S = (1, 3, 4)$$. 

In this case, the start position is always **N position** since the next person 
can take all the things together, 0 must be a **P position**. 2 must be a **P position**
since the only leagal move is to **N position**...

---

#### Nim Sum and the proof ####

Now we define a binary operation called **Nim sum ($$\bigoplus$$)**, which is simply adding 
the binary representation of numbers together in a way that:

$$ 1+0=1=0+1$$ and $$ 1+ 1=0=0+0$$

We note that any $$x \oplus x =0$$, we provide the following proof of Nim:

**Theorem**: The winning stratege in normal nim play is to finish every move 
with a Nim-sum of 0.

**Lemma 1:** If the Nim-sum is 0 after a player’s turn, then the next move
must change it.

Assume that we have $$n$$ heaps with $$x_{1}, x_{2}, ...,x_{n}$$ number of objects in each heap.
The Nim-sum of all the heaps before the move will be:

$$S = x_{1} \oplus x_{2} \oplus ... \oplus x_{n}$$

Then we define the Nim-sum of all the heaps after the move:

$$T = y_{1} \oplus y_{2} \oplus ... \oplus y_{n}$$

If $$S =0$$, there is a $$y_{m}$$ after the move that $$y_{m} \neq x_{m}$$,
and the rest piles does not change. Then we have:

$$ \begin{aligned} 
T &= 0 \oplus T \\
&= S \oplus S \oplus T \\
&= S \oplus (x_{1} \oplus x_{2} \oplus ... \oplus x_{n}) \oplus (y_{1} \oplus y_{2} \oplus ... \oplus y_{n}) \\
&= S \oplus (x_{1} \oplus y_{1}) \oplus (x_{2} \oplus y_{2}) \oplus ... \oplus (x_{m} \oplus y_{m}) \oplus ... \oplus (x_{n} \oplus y_{n}) \\ 
&= S \oplus x_{m} \oplus y_{m}

\end{aligned}$$

Hence if we started $$S = 0$$, $$T$$ must be non zero since $$x_{m} \oplus y_{m}$$ will never be zero.

**Lemma 2:** It is always possible to make the nim-sum 0 on your turn if
it wasn’t already 0 at the beginning of your turn.

Lets say we started from the above position which is non-zero. We are making a move 
so that $$y_{m} = S \oplus x_{m} $$. Hence we need to remove $$x_{m} - y_{m}$$ stones 
from the heap.

$$ \begin{aligned} 
T &= S \oplus x_{m} \oplus y_{m} \\ 
& = S \oplus x_{m} \oplus S \oplus x_{m} \\
& = 0
\end{aligned}$$

**Proof:** If you start off the game by making the Nim-sum zero, then 
on each turn your opponent will make the nim-sum non-zero and you can
reset it back to zero. Eventually on your turn there will be no stones
left with a nim-sum of 0. 

**Proof for anti-nim:** In this case you want to set the sum to 1 instead of
zero.

End of proof