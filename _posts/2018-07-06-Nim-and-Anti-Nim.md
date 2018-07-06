---
layout: post
title:  "Nim and Anti-Nim"
tags: [Fun, Algorithms]
---

From [wiki](https://en.wikipedia.org/wiki/Nim):

> **Nim** is a mathematical game of strategy 
in which two players take turns removing 
objects from distinct heaps. On each turn, 
a player must remove at least one object, 
and may remove any number of objects provided 
they all come from the same heap. The goal of 
the game is to be the player who removes the 
last object.

---

Game play:

There are three piles, or nim-heaps, of stones. Players 1 and 2 alternate
taking off any number of stones from a pile until there are no stones left.
There are two possible versions of this game and two corresponding winning
strategies that we will see. Note that these definitions extend beyond the
game of Nim and can be used to talk about impartial games in general.

• **Normal Play** The player to take the last stone (or in general to make
the last move in a game) wins. This is called normal play since most
impartial games are played this way, although Nim usually is not.

• **Misere Play (Anti-Nim)** The player that is forced to take the last stone loses.