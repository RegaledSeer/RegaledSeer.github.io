---
layout: post
title: To Document or Not to Document: A Look into the Documentation Debacle
published: false
---

One thing I find incredibly interesting is the debate between extensive 
documentation and commenting versus the "self-documenting" code base. 
There are people who [embrace documentation](http://www.htmlist.com/development/the-bane-of-documentation/), 
and some of those people [believe self documenting code is a myth](http://ericholscher.com/blog/2017/jan/27/code-is-self-documenting/). 
On the flipside of the coin, there are people who think 
[documenting code can be misleading](https://visualstudiomagazine.com/articles/2013/06/01/roc-rocks.aspx), 
and perhaps there is a good reason: "Comments lie to you", as 
Northeastern's beloved Matthias Felleisen once told us in class. 
Yet Matthias is a *very* strong advocate of documenting code. 
But are those two concepts the same, and if so, is he being hypocritical? 
What's the difference? To some new programmers, it can be confusing to 
think about the two.

### What is documentation?

What is documentation, and what is a comment (For those of you who know the 
difference, feel free to skip ahead)? Code documentation, boiled down to its 
simplest concept, is writing in a human language to describe what a particular 
bit of code does. You could think of it as a piece of metadata attached to 
your code that more or less gives you an insight in how the original 
programmer **intended** to use the code. Comments, on a similar vein, are 
snippets of text that a programmer can insert anywhere in the code and can 
be used to talk about *anything*, including a programmer's intent. Wait, 
now I'm confused. What's the difference? I personally was confused when I 
first started learning about documentation and comments, so it's a good idea 
to clear this up before going on.

Documentation is metadata you use to describe code and its purposes. 
It helps you capture the intent of a programmer because sometimes code 
can be complex or it could be interpreted in another way that the programmer 
did not foresee. Let's take an example here.

```python

def foo(bar, x):
	bar.initialize()
	bar.config("localhost")

	while x:
		for z in x:
			bar.send(z)
			if len(z) == 0:
				return -1
		x.drop()
	
	bar.clean_up()
	return 0
```

This is a pretty exaggerated example (I just came up with it on the spot), 
but it does a pretty job of describing what it feels like to be on the end 
of a maintenance programmer. Granted, the names may actually be somewhat 
descriptive (*some* of the time), but to me, that's essentially what it feels 
like to read someone else's code. The worst (or best, perhaps) thing about 
Python is that through dynamic typing, we have no idea what this function is, 
what it computes, or what the inputs are! This could be entirely catastrophic 
and poorly documented code like this could be disastrous for a future 
programmer (whether it is yourself, someone years later, or 
even your colleagues).

Now, let's look at a slightly improved version of this:

```
def foo(bar, x):
	"""Sends ping packets to a list of IP addresses.

	Args:
		bar (Ping): Used to ping ip addresses
		x (list): Contains a list of strings representing IP addresses
	Returns:
		int: 0 if successful, -1 if given an empty IP address
	"""
	bar.initialize()
	bar.config("localhost")

	while x:
		for z in x:
			bar.send(z)
			if len(z) == 0:
				return -1
		x.drop()
	
	bar.clean_up()
	return 0
```

Now it makes a *little* more sense. Granted, this code could be further 
improved by choosing appropriate variable names and restructuring the code 
(barring whatever inefficiencies there are in the code). Nevertheless, it 
is *especially* important to note what the types are in dynamically typed 
languages like Python, where any interpretation of a variable could cause 
the entire program to go haywire.

But what about languages like Java? Do we really need documentation for that 
too? Yup. Even if we gain type information thanks to static typing, do you 
really trust a future programmer to know *exactly* what you meant by just 
looking at your code? Okay, so what? Just because someone can't understand my 
code, does that mean I still have to document code? That's just your ego 
talking if you genuinely think that: There's a good chance that you'll forget 
what your code does too. A good rule of thumb is try and consider looking 
back at your code in 6 months' time. If you can't understand it, then you 
have likely written poorly documented code.

That's not the endcase for documentation, but rather it's a little taste of 
what documentation does for your code.

### What are comments?

Comments are, like I said before, snippets of text that you can implant 
anywhere in the code. Let's look at an example:

```python

def read_file(f):
	with open(f, 'r') as file:
		#should be a JSON file
		x = file.read()
```

This is an example of a comment, but whether it is a good or bad comment 
depends on one thing: Are you answering why you left a comment here? Many 
programmers that I talk to from the industry tell me that comments lie. But 
how can comments lie? What does that even mean?

Let's say we have this code snippet that we inserted as a "hack" in our code 
base:

```python

def fix_array(l):
	a[0] = 8
	
	# this element should be odd
	a[-1] = 29
	return l	

def foo():
	l = [0] * 100
	l = fix_array(l)
	if l[-1] % 2 == 0:
		return True
	return False
```

At the moment, the code works as we intend it to! What is it's intention? I 
have no clue, I must've wrote that back in 2015, can you expect me to 
remember what it does?

Let's say a maintenance coder then decides to fix the array function:

```python

def fix_array(l):
	a[0] = 9
	# this element should be odd
	return l	

def foo():
	l = [0] * 100
	l = fix_array(l)
	if l[-1] % 2 == 0:
		return True
	return False
```

Through some vague interpretations, the maintenance programmer decided that we 
could reduce some lines of code to make things more efficient. Well, it looks 
like the code is buggy now, but why? I have no clue, but when I investigate 
the reason, I might come to the conclusion that `a[0]` was meant to be odd. 
Maybe this could be fixed by implementing a VCS, but what happens if we 
haven't tested this functionality for ages, and the code removed was passed 
off through several versions? I would hate to be the guy who tries to hunt for 
that bug.

Another one of my personal favorites is the comment that tells you to never 
touch the code:

```python

def foo(x=[],y=1.2,z=None)

	#DO NOT TOUCH!! Will break if you modify anything
	...
	...
	..
```

Suppose we had a bug in this function. Well, upon looking into the function, 
I would find that the programmer a) had no clue what they were doing, b) was 
in a rush and couldn't implement something better in time, or c) knew what 
they were doing, but didn't bother giving me a reason why I shouldn't touch it.

In fact, comments are generally good for one thing: Telling me *why*. The 
documentation can give me the intent, but the comments could give me the 
reason. If I were to use a bubble sort algorithm over a merge sort, how 
can I tell you that the bubble sort function also does something else, and a 
merge sort would complicate things? Simple: A small, sufficient comment.

## The self documenting code

So why did I go through the trouble of describing what documentation and 
comments are, and what they should do? Well, there's actually another school 
of thought, which is the *self documenting code* paradigm. It should be 
self-explanatory (obviously) as to what it is.

But what if it isn't? What if that last sentence wasn't clear enough to the 
reader? Someone subscribing to the philosophy would just say: Make it 
clearer. Let's see an example:

```python

def draw_square(x_pos, y_pos, pen):
	pen.move_to(x_pos, y_pos)

	pen.orient(0)
	pen.move(10)
	pen.rotate(90)
	pen.move(10)
	pen.rotate(90)
	pen.move(10)
	pen.rotate(90)
	pen.move(10)
	
	pen.lift()	
```

It's pretty good, right? Pretty clear as to what it's doing: We're taking a 
pen and drawing straight lines, then rotating 90 degrees each time. There 
can't be anything wrong, can there?

Well, do we know *exactly* what `x_pos` and `y_pos` are? Are they integers? 
Are they position objects? Are they strings? Maybe in Java or similar 
languages, it wouldn't matter, but how can we tell a reader that the rotate 
function works in 360 degrees, only? Or what happens if we were to rotate past 
360 degrees? If we have no knowledge of the implementation of `rotate()`, then 
we would be hard pressed to *not* guess what the program is doing, and when a 
programmer has to guess what you are doing, that's where bugs happen.

Granted, there is an argument in which many self-documenting code activists 
love to champion, though.

## Code readability and overdocumentation

Yes, documentation carries an overhead: *visual space* in the source code. 
There's no denying that by adding in comments, you add in extra text that 
could potentially make it harder for developers to read the code.

#TODO: Talk about how my school does documentation right and teaches good documentation

#TODO: Go into my thoughts about code size and how comments could possibly bloat the code base and make it ugly

#TODO: Give them an example of shit code, then write comments for shit code, then explain why self documenting
# AND documentation would be the perfect combination for coders
