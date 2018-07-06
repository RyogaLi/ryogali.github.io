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

• **Normal Play** The player to take the last stone (or in general to make
the last move in a game) wins. This is called normal play since most
impartial games are played this way, although Nim usually is not.

• **Misere Play (Anti-Nim)** The player that is forced to take the last stone loses.

---

Types of impartial game positions
• A game is in a **P-position** if it secures a win for the Previous player
(the one who just moved).
• A game is in a **N-position** if it secures a win for the Next player.

Then we can think about this problem as **backwards induction**. The **terminal position**
of this game is always $$(0, 0, 0)$$ and we can label this as the **P-position**
And that any position $$(0, 0, n)$$ is an **N position**.

Lets say we have three heaps: $$S = (3, 4, 5)$$. 

In this case, 
