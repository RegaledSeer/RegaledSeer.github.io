---
layout: post
title: Why I love the Felleisen introduction to CS.
categories: [general]
tags: [felleisen, northeastern, introduction]
description: My rant on the introductory courses at Northeastern
---

Coming from Northeastern, I can say for sure that anyone who has heard the 
horrors of [Fundies 1](https://course.ccs.neu.edu/cs2500/) can relate to the 
struggles that our introductory course has brought to people who have both 
learned CS before college and people whose first coding experience was with 
[Racket](https://racket-lang.org/).

For those of you who aren't from Northeastern, our flagship introductory 
course to computer science is our Computer Science Fundamentals 1 & 2 (dubbed 
"Fundies 1" and "Fundies 2" in our school), each of which are a semester long 
(with Fundies 1 being a prerequisite to Fundies 2). A typical CS courseload 
for a freshman is typically taking Fundies 1 and Discrete Structures in the 
fall semester, and then taking Fundies 2 and Logic & Computation in the Spring, 
often followed by Object Oriented Design in either summer course or as a course 
as a sophomore in the following fall semester, thus generally the path looks 
like this:

> The Felleisen Path: Fundies 1 & Discrete Structures -> Fundies 2 & Logic -> Object Oriented Design

One of my [favorite professors](https://www.ccis.northeastern.edu/people/benjamin-lerner/) 
told me in Fundies 2 that this path is the architecture of our 
beloved [Matthias Felleisen](https://www.ccis.northeastern.edu/people/matthias-felleisen/). 
Matthias's philosophy was to break any notions that high school students would 
have with computer science (Computer science is **not** programming, 
for instance), and introduce them to formal computer science. In fact, I was 
one of those kids who thought he could pass off as a skilled computer scientist 
thanks to my previous programming experience. Little did I know, I was in for a 
wild ride for my freshman year.

Too many people relate computer science as an academic discipline to computer 
programming, a practice field that is related to computer science. Yes, 
many in the industry will require that you have a computer science degree 
before applying to their companies, but it is *not* a direct translation of 
programming skill if you simply have a computer science degree. One of my 
first misconceptions when going into Northeastern was that my programming skill 
would be a direct benefit to doing well in Fundies 1 and 2. In fact, the only 
skills that benefitted me in the courses was a little problem solving I gained 
when doing USACO challenges (although most of the problem sets were less focused 
on algorithmic challenges for both Fundies 1 and 2), and some knowledge of 
Java syntax in Fundies 2.

So what's so different about Fundies 1 and 2 that make me love the courses so 
much? As I have mentioned before, Fundies 1 introduces basic concepts for 
learning computer science through a language called Racket. We use a subset of 
languages of Racket, called "BSL", and "ISL" ("Beginning Student Language" and 
"Intermediate Student Language", respectively). Racket's a pretty unique 
language in that it is a multi-paradigm language that is fully capable 
of [creating completely new languages](http://users.eecs.northwestern.edu/~stamourv/papers/languages-the-racket-way.pdf), 
thus you make languages that support a subset of Racket's language, like 
BSL and ISL that are great ways to start teaching students what computer 
science is like. We even created a basic implementation of HTML in Racket in 
one of our labs once!

So what is Racket, really? Well, this is probably my favorite part about 
Racket: Racket, although being a multi-paradigm language, is heavily 
influenced by Lisp and Scheme and has a strong focus on functional 
programming, although it [can support imperative programming too](https://docs.racket-lang.org/guide/for.html). 
In Matthias' eyes, students should "first learn computer science by relating 
it to their experience in high school STEM courses". In particular, math 
courses are a strong asset for first learning about computer science. Let's 
look at an example of what Racket has to offer:

```
; Number Number -> Number
; adds two numbers together and returns it sum
(define f (x y)
    (+ x y))


(check-expect (f (5 8)) 13)
(check-expect (f (-1 0)) -1)
```

This is admittedly a simple example, but it's a great way of teaching 
high school students how to think functionally. All code has to exist in a 
function, or as a variable. Just like in high school math, all the operations 
that students do are generally defined in functions, and there is no notion of 
changing "state" between function calls (a function is defined as a unique 
input always leading to the same output). There are concepts of "global" 
values with variables, but they don't generally change (we used these global 
variables as constants essentially). There are too many concepts that Fundies 
1 introduced that cannot be covered in a single blog post (Students learn the 
infamous "[Design Recipe](https://course.ccs.neu.edu/cs5010sp15/recipe.html)"), 
but a lot of the thinking about how to create functional programs are taught in 
Fundies 1.

I remember how simple I thought the course would be after the first lesson, 
but after taking a few more lectures during the semester, I realized that 
Fundies 1 was *really hard*. We ended up learning about abstraction, 
recursion, and even solving algorithmic challenges using functional 
programming. I don't know if I would ever want to solve the N-queens problem 
using functional programming again, but it was a pretty rigorous problem.

I personally think that learning functional programming first is a great way to 
think about computer science as a *discipline*. Yes, there are *very* good 
developers who [argue that students should learn how to program in C before moving on to higher level concepts](https://www.joelonsoftware.com/2001/12/11/back-to-basics/), 
but I think it would be best to show students that computer science is *not* 
telling a robot how to walk 15 steps in a direction, but rather it's about
 *solving mathematical problems* and *abstracting real life concepts* to make 
them computable. Fundies 1 teaches you how to do exactly just that, and is a 
great way to think of computer science as a scientific discipline. After all, 
computer science *is* a branch of mathematics 
and [even existed long before the discovery of computers as we think of them today](https://en.wikipedia.org/wiki/Computer_science#History).

One thing about Fundies 1 in our school is that it contradicts the general 
path that computer science students in other schools (e.g. CMU, MIT, 
Stanford, just about any other school) takes, in which they use a generally 
popular language like Java or Python ([Joel makes an interesting argument about learning those languages first, by the way](https://www.joelonsoftware.com/2005/12/29/the-perils-of-javaschools-2/)), 
and learn how to solve algorithmic problems, sort of like a 
"precursor to Algorithms". I really like the Fundies 1 method more, as it 
had taught me how to comfortablly handle recursion and induction which 
[many computer scientists should not struggle with](https://medium.freecodecamp.org/learn-recursion-in-10-minutes-e3262ac08a1). 
A lot of students that I've talked to from other schools don't really get 
recursion and somehow managed to get by without a thorough understanding of 
recursion, but students from schools like WPI who [also learn Racket](https://web.cs.wpi.edu/~cs1102/a11/Lectures/) 
*do* get recursion, so it seems like Racket does a fine job of teaching 
recursion.

Now, I've only been mentioning Fundies 1 since it is practically our flagship 
introduction course (which also happens to be the equivalent of our weed out 
course, since many students struggle with Fundies 1), but this is just part 1 
of the "Felleisen way". In fact, during the time students usually take Fundies 1, 
they're also taking Discrete Structures, which there really isn't much to say 
about, sadly. Discrete Structures is more akin to a typical discrete math 
course that most students take, so there's not much to say that is unique 
about our course.

Students typically take these two courses together, eventually culminating in a 
strong foundation for computer scientists. After the fall semester is over, 
most CS majors go on to take Fundies 2 and Logic & Computation, which is 
another unique set of courses.

Fundies 2 is an interesting couse: It takes the philosophies of Fundies 1 (the 
functional programming "thinking") and converts it into Java—in fact, 
many students say that Fundies 2 is essentially a follow up to Fundies 1 
but in Java. It's pretty unique in that a lot of the foundations taught in 
Fundies 1 are translated *roughly* in Fundies 2, but with the interesting 
dilemma that Java, being a generally imperative and object-oriented language, 
doesn't truly match Racket's design. While I say that Fundies 2 tries to 
teach Fundies 1 through Java, that's not entirely true: Fundies 2 tries to 
teach the *problem solving* acquired from Fundies 1, but provides an 
introduction to class-based design used to solve these problems. 

Fundies 2 also helps reinforce the "test-driven development" philosophy that 
Fundies 1 introduces, but perhaps even more rigorously. In Fundies 1, we are 
taught to write test cases for every edge case we could think of, but with the 
caveat that an input will always supply the same output. With Fundies 2, we are 
introduced to mutation (which is pretty unique given that most students from 
other schools are taught about mutation in their introductory course), thus we 
need to check for mutation as well.

In conjunction with Fundies 2, CS majors would then take a course called "Logic 
& Computation", a course which is nearly despised by all students (partly 
because it can be an incredibly boring course), but I happened to enjoy it 
(I signed up to be a TA shortly after completing the course)! Logic and 
computation focuses on proving functional correctness in a language that is
 *very* similar to Racket, but is entirely functional. This language is called 
ACL2s and is generally make or break for most students who take the course. 
ACL2 implements a fundamental axiom by ensuring that *In a problem, every 
input will always return the same output*. This is pretty significant, 
because now we can prove trivially *functional correctness* for many functions 
that we define.

The course itself was a strong method to reinforce what we learned in 
Fundies 1, and I could tell you personally that I don't really remember 
much of the syntax from Racket, but using ACL2s helped me remember about 
functional programming and in particular helped me re-learn some concepts from 
Fundies 1 that I had struggled with when I first took that course. It was a 
rather interesting course in that while most students would say it was a 
"useless" course for them, it taught me about using contexts and conditions to 
prove that a program will be correct *every single time*. Using unit tests are 
pretty essential for development, but mathematically it will not prove every 
case. Proving that a program is correct using logic and mathematical proofs 
will cover *every case*, and that is pretty powerful.

Lastly, most students will opt to take Object Oriented Design in the fall or 
summer. We are taught the classic design patterns that the Gang of Four have 
written about, and we are also taught how to write designs that are focused 
on future-proofing our applications while also learning hot to make tradeoffs 
in our design. To be honest, this is probably the most *practical* course that 
you could take in our school, as it directly benefits your ability in the 
industry to design systems that can be maintained by future programmers. The 
most interesting thing to note about this course is that it strays away 
from everything Fundies 1 and 2 have taught you (In Ben Lerner's words, 
"Everything you learned in Fundies 2 is wrong"). Being taught object-oriented 
programmming strays pretty far from object-oriented programming, but it was a 
rewarding challenge to strech your mind in thinking in two different paradigms.

So, what was the purpose of all these courses and why are they taken in such a 
particular order? Ben Lerner explained this to me after our final exam in 
Fundies 2. Matthias' philosophy was to take a high school student and turn 
that student into an analytical computer scientist who was capable of making 
large applications. You might be wondering about the rant I mentioned about 
computer science being an academic discpline. I would be lying if I said that 
our school wasn't practically driven: Our school is famous for its flagship 
coop program. Personally, I think that the skills we take from learning how to 
analyze problems and turn them into computable problems is the most powerful 
skill we can take in applying our CS skills for the industry.

 In Fundies 1, we are taught to make applications that can sustain hundreds of 
lines of code without the codebase being incredibly difficult to maintain. In 
the meantime, we are also taught to take computer science as a scientific 
discipline thanks to Discrete Structures. In Fundies 2, we are taught how to 
make applications that can sustain thousands to tens of thousands of lines of 
code before it starts becoming too much to maintain, with Logic and 
Computation helping us reason about our code to ensure that we can use 
invariants to expand our computing capabilities. Finally, in OOD, we are 
taught the basics of making *libaries* and *maintainable, large-scale code*, 
which expands our programming ability to now make codebases of millions of 
lines of code.

This was the entire philosophy that Matthias had strived to achieve for 
Northeastern students, and while there were definitely moments that I truly 
struggled with the courseload, I came out of the year feeling as though I had 
actually learned something. Yes, we aren't the most theory based school 
(particularly because we *are* focused on practical skills acquired), but we 
do a pretty bang up job of teaching computer science *and* programming, 
despite being a university and not a trade school. I really appreciate the 
core courses I've had to take for Northeastern, and I'm excited to take some 
of the more traditional course that Northeastern has to offer for computer 
science, although I do miss the uniqueness that Fundies had to offer!
