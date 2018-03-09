---
title: "Book Review: Test Driven Development By Example"
slug: "book-review-test-driven-development-by-example"
tags: ["TestDrivenDevelopment", "TDD", "Apprenticeship"]
date: 2018-03-09
---

I already wrote a lot about test driven development, but I can't hold myself back to writing more.

Today, I finished reading [Test Driven Development By Example](https://www.goodreads.com/book/show/387190.Test_Driven_Development) book by [Kent Beck](https://twitter.com/KentBeck). Developers with different level of experience can take from the book. Author created an adequate entry point for TDD, while keeping the book interesting by explaining various patterns we can benefit every day.

Author starts with a real-life use case, that you want to read at once. In this part, author refactors a system by the help of TDD. Keeps shocking us by faking the implementation, and committing programming sins while reminding us importance of getting to `green` as quick as possible. Afterwards, by defining similarities and separating differences, the sins fade away, classes and patterns arise instead. The simplicity behind the TDD makes us to write exact amount of code we need.

Right after shocked with a fast-paced introduction, the author makes us think about testing frameworks. Honestly, I have never wondered how `jUnit`, `jest` or any other test framework works -my bad-, I treated them as if they were existed since the Turing Machine. In the second part of the book, author reveals the mystery for me by developing a test framework with TDD.

After two different practices, at part three, author defines patterns for different stages of TDD. In almost every pattern, there is some example code to make it easier to understand. This part is the toolset we need to get better on TDD.

### It's All About Feedback.

The more feedback we get from our code, the more we will be confident with our work. The author points on this accurately with the feedback loops he defined between `stress` and `testing`.

Also in a chapter, author shares how he blessed her daughter with TDD:

> I taught Bethany, my oldest daughter, TDD as her first programming style when she was about age 12. She thinks you can’t type in code unless there is a broken test. The rest of us have to muddle through reminding ourselves to write the tests.

I wonder how different the software world would be if we have learnt programming with TDD at first place.
