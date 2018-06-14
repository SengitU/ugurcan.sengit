---
title: "The Zone"
slug: "the-zone"
tags: ["CleanCoder", "TDD", "Javascript", "apprenticeship"]
date: 2018-06-14
---

In the **Clean Coder** book, Robert Martin has a section dedicated to explain _The Zone_. _The Zone_ or _The Flow Zone_ is a hyper-productive state which one can feel focused during this period. But, there is a catch, the zone blinds you slowly. Inside the zone, you become more and more focused on that individual problem, meanwhile you slowly lost your perception for the project itself. Slowly you become obsessed with that individual solution and lost your sight, until someone help your way out of the problem.

Inside the zone we start to push that individual solution, the code snippet we know we need to write. In these desperate times, TDD is always there to save us. Because TDD is all about letting the tests to drive the code, if you actively use TDD, you will never want to write the code snippet you know you need to write. Instead of struggling, you will simply follow the breadcrumbs.

Recently I've pushed my very first commits into a new codebase. It's a huge codebase with more than 8k unit tests. In that individual module which I needed to contribute, I found the traces of a colleague from the inside of _the zone_. If you are inside of the zone, you want to push your solution, therefore tests leave the steer. Since we can't push our codebase without 100% coverage, then we need to provide 100% percent coverage with an untestable solution. Right at this moment, tests lost their meaning.

I would like to clarify that, I am not judging any other individual. I've done the mistakes I defined above. I wrote ugly tests cases with nested callbacks and lazy assertions. But they only help you to pass the coverage limit, afterwards they start to poison the project until the end of the days.

Stay out of _the zone_ as much as you can. Apply TDD, ask for help, do pair programming, there are so many ways to stay out of the zone. But most importantly, do not write a single line of code unconsciously.
