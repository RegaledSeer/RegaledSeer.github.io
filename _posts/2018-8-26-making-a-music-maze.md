---
layout: post
title: My Thoughts in Making a Music Maze
published: false
---

Notes to be left for publishing:

* Initially didn't think that the maze generation would be too hard
* Looked up various algorithms like Eller's, Kruskal, Prim
* One day during the commute, realized there was an issue: What am I trying to do?
* Goal of the maze was to originally go end to end
* the solution required a very specific length
* Thought about finding a diameter of a MST with such a length
* Turns out it was a hard question and is something done in research
* Then thought about possibly just any path going end to end with a length
* But how big should we make the maze then?
* Were there any heuristics that we can use?

* Rephrased the question: Can I generate a random path from an edge?
* One idea I thought of was to just randomly generate a path from end to end
* This turned out to be a hard and inefficient problem with random generation
* I later decided to think about just picking one of the edges from the maze
* and then randomly walking the maze until the length was exhausted
* Then a MST can be built from that solution.
* One issue is that I still don't know how big the maze will be exactly
* Also a big part of the maze is still left untouched if done incorrectly.

