---
layout: post
title: Duck Typing, Interfaces, Contracts, and You.
---

I recently took a [rather wonderful course](https://course.ccs.neu.edu/cs3500/) that got me thinking about good object oriented programming, and like many aspiring CS students, I tried to actively apply what I learned from OOD and use it in a project. One project that I like to work [on during my commutes](https://github.com/RegaledSeer/PyBoardGames) is the PyBoardGames project. At the moment, I'm working on the chess game and implementing various chess pieces.

In this particular project, I chose to implement the project entirely in Python, making development rather interesting. With Python being a dynamic, strongly typed language, it presents an interesting array of challenges with regards to designing with OOP in mind. One problem that I encountered and got me thinking was the concept of using interfaces to promote [dependency inversion](https://www.oodesign.com/dependency-inversion-principle.html) in my project. 
