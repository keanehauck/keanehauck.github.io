---
layout: page
title: "Investigations into 3-color Peg Solitaire"
date: 2024-05-16
summary: Analyzing the solvability of variations of classic peg solitaire.
tags: research, game theory, peg solitaire, proofs
---

The game of peg solitaire has a rich and complex history. Many are familiar with the game and its seemingly simple rules: “jump” a peg and it disappears, and repeat until there is one peg remaining. However, a deeper analysis of peg solitaire reveals rich mathematical ideas behind both the strategy and solvability of the game. Boards can come in many different shapes; the most prominent of which have been listed below:

![Peg Solitaire Board Shapes](/images/research/peg-solitaire/boardshapes.png)

On the first 5 board layouts, moves are made by jumping pegs either horizontally or vertically. The 6th board, however, allows jumps in 6 different directions: one for each side of the hexagons. The solvability of these boards is well-established; however, less work has been done on different variations of the game. Our research focused specifically on peg solitaire in 3 colors on a triangle graph.

Analysis on traditional peg solitaire on triangle boards (board 6) can be found in the work of George Bell, who published a paper in 2008 titled “Solving Triangular Peg Solitaire.” My
advisor and I extend this work to a variation on the traditional rules where the concept of “colors” is introduced to the graph. The normal game of peg solitaire can be conceptualized as having two colors: one for an empty hole and one for a peg. We added a third color to the game, representing a different color of peg. Under this new ruleset, if a peg is jumped over a peg of the same color, the peg that was jumped over switches to be the other color. If a peg is jumped over a peg of a differing color, the jumped peg is removed as normal:

![3-Color Rules](/images/research/peg-solitaire/3color.png "Davis et al., 2020")

Adding this ruleset drastically changes what we know about the solvability of different types of graphs. My advisor and I have proven the solvability of all boards of height 4 and 5, and have inductively proven the number of starting positions on triangle boards up to symmetry.

A brief write-up of our work can be found [here.](/images/research/PegSolitaire.pdf)

