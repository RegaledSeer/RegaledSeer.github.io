---
layout: post
title: Duck Typing, Interfaces, and You.
---

I recently took a [rather wonderful course](https://course.ccs.neu.edu/cs3500/) that got me thinking about good object oriented programming, and like many aspiring CS students, I tried to actively apply what I learned from OOD and use it in a project. One project that I like to work [on during my commutes](https://github.com/RegaledSeer/PyBoardGames) is the PyBoardGames project. At the moment, I'm working on the chess game and implementing various chess pieces.

In this particular project, I chose to implement the project entirely in Python, making development rather interesting. With Python being a dynamic, strongly typed language, it presents an interesting array of challenges with regards to designing with OOP in mind. One problem that I encountered and got me thinking was the concept of using interfaces to promote [dependency inversion](https://www.oodesign.com/dependency-inversion-principle.html) in my project. Ideally, I would have various classes that all implement an interface, allowing me to promote good design, but the lack of an interface and the lack of static typing making this an interesting challenge.

As it turns out, Python does have [abstract base classes](https://www.python.org/dev/peps/pep-3119/), but just like in C++, it feels a bit awkward to artificially implement interfaces using abstract base classes that only have methods. Moreover, you can't really enforce that a function will take a specific object since duck typing throws away the entire notion of a static type, making it really hard for me to infer what the types should be.

I was struggling to come up with a proper solution to this issue, when I realized that this was a challenge to all dynamically typed languages in general. How do other languages deal with this problem? Surely, there could be some sort of tried and tested method that Pythonistas generally work with when dealing with OOP in Python. As it turns out, there isn't even a need to worry about this, and many Python programmers don't even bother with worrying about interfaces in the "Java" sense!

Coming from a Java background in OOD, I have been working with interfaces throughout all of my CS career. Of course, I have had experience in Python with regards to scripts and CTF solutions, but I have never used it to develop an application using OOP. I had the wrong mindset for the situation, in fact: I need to be embracing duck typing, rather than trying to develop a Python application with a Java mindset. Let's establish what "duck typing" really is.


This could probably be best explained in an example:
```python

class Duck:
    def walk(self):
        print("Duck is walking")

    def quack(self):
        print("Quack")

class Goose:
    def walk(self):
        print("Goose is walking")

def duck_walk(duck):
    duck.walk()

def duck_quack(duck):
    duck.quack()
    
d = Duck()
g = Goose()

duck_walk(d)

#It doesn't matter what type of object is supplied, so long as it has a walk() method
duck_walk(g)

duck_quack(d)

#This will be the only function that raises an error, as Goose does not have a quack method
duck_quack(g)
```

If you've never learned about duck typing before, it essentially follows this premise:
> If it walks like a duck and it quacks like a duck, then it must be a duck

Python's duck typing emphasizes an object's *behavior* over an actual class, which is a dramatic difference to something like Java, whose compiler would yell at you if you were to try and provide dramatically different classes to functions that expect a specific type of object. Because of this, it requires a completely different mindset when dealing with Python objects. Granted, there *technically* is the `isinstance()` operator, but this is discouraged in practically every case in Java, and is *especially* discouraged with duck typing for Python, since we shouldn't be worrying about what the type is, but rather let the "duck" walk and quack for itself.

Now, with this new found knowledge of duck typing, what could I do with interfaces and promoting dependency inversion? Hmm. It looks like we're still stuck on the same page, since now that we know that *any* object could be used, it seems like we're not getting anywhere. The rationale I could come up with after looking around the web was to **document and test**.

 It's a bit disappointing that this is the most optimal solution to the issue, but this is a drawback to using dynamic typing: Our interfaces are *implicit*—not explicit. In order for us to even use these interfaces, we have to document it and explicitly mention to the programmers what kinds of objects are expected, and hope that these programmers will follow the documentation. In order for us to *prove* that our code provides an expected output, we *have* to unit test to show others that our code will return what is expected. It kind of sucks, but this approach more closely resemble Guido's philosophy of letting programmers do whatever they want, since "we're all consenting adults here".

This project has been interesting in terms of learning about the capabilities and limitations of dynamic typing, and I hope that I will encounter some more practical challenges that come with using Python as an OOP code base.
