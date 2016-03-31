---
title: Genetic Algorithms for Fun and Profit
updated: 2016-03-30 20:18
---

![DNA strand](/assets/img/dna-strand.jpg)

The aim of this article is to give total beginners a little background on what genetic algorithms are, why they're cool, and how to implement a really simple example. The code snippets are written in JavaScript, but it should be easy enough to follow in whatever language you choose.

<!-- First, a little primer on how natural selection works.

>
>
>
> -->

So what are genetic algorithms? If you browse the [Wikipedia page](https://en.wikipedia.org/wiki/Genetic_algorithm) you'll learn that they're not really *algorithms* so much as they are *heuristics*: that means that a genetic algorithm will probably not give you the most efficient solution to a problem, it will try to approximate it. The ways in which a genetic algorithm tries to solve a problem are a simplified version of how natural selection works: the solutions reproduce, mutate, and potentially die off if they are not fit. Let's pick a simple problem to solve:

> Given digits 0 through 9 and four operators +, -, *, and /, find an expression that will result in the target number.

One of the first things we have to do is figure out how to encode a solution into something that will function like DNA. We want it to be able to mutate and cross over during reproduction. There's a couple of options:

```js
binaryBitString = '10001100101101011110101001';
// when decoded, this will represent a solution to the problem.
```

The bit string is pretty useful because it is easy to splice and mutate - the only annoyance is that we have to write some sort of parsing functions to convert it into a solution. We could do something that's simpler:

```js
randomSolution = [3, 1, +, 9, 0, -, 2, 2];
```
