---
title: "Pitfalls in Software Development"
slug: "pitfalls-in-software-development"
tags: ["DesignPatterns", "Pitfalls", "Apprenticeship"]
date: 2018-03-15
---

Yesterday I had a discussion with [Pinar](https://twitter.com/pinarkaymaz6) about pitfalls that one could fall in software development. We talked about the diamond problem, and the conversation started my train of thought.

Basically, the diamond problem is the situation when a class needs to have behaviours from two separated base classes. Assume that we have a `LivingThing` class with `breathe` function. There is an `Animal` and `Reptile` classes derived from `LivingThing`. While you are happily living with you `Reptile` and `Animal` instances in your project, clients want to have a `Snake` class, which is both animal and reptile, so which `breathe` function will be used? Different programming languages has different technical difficulties, in C++ you can apply multiple inheritance in such case, but you will end up with compilation error. In general, you should define your behaviours as interfaces, or functions and compose your current class with behaviours.

So, is the inheritance evil? I think it's not. We benefit from inheritance as long as we use it carefully and keep them flat. If we do not keep them flat, we will end up with the monkey-banana problem, let's write about it another day.

Getters could expose internal state of a component for mutation, then should we skip using them at all? Of course not. But, it's important to know upsides and downsides the techniques we are using. 

> We need to know common pitfalls as well as we know the design patterns.

Throughout our journey in software development, today's important concepts will become obsolete and new concepts will arise. We must keep ourselves up to date to make important trade-off's when the time comes.

I would like to share some resources that would help a lot.

[Detailed example on diamond problem](https://medium.freecodecamp.org/multiple-inheritance-in-c-and-the-diamond-problem-7c12a9ddbbec)

[Getters/Setters. Evil. Period.](http://www.yegor256.com/2014/09/16/getters-and-setters-are-evil.html)

[Composition over Inheritance](https://medium.com/humans-create-software/composition-over-inheritance-cb6f88070205)
