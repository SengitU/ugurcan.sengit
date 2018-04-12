---
title: "The Simplest Test Framework"
slug: "the-simplest-test-framework"
tags: ["Test", "Frameworks", "Apprenticeship"]
date: 2018-04-05
---

In Test Driven Development By Example book, Kent Beck writes a simple test framework from scratch by using TDD. This inspired me to practice and to create my own test library. But, I had no idea where to start. Even if I find a place to start, I would somehow need to figure out how to write unit tests, while testing framework is under construction. My mentor, [Wolfram](https://twitter.com/wolframkriesing), guided me again.

Together we thought about testing frameworks. He asked me questions about fundamentals, which we usually don't think about. We started to write down essentials of a test framework. We ended up with four aspects;

* Assertion
* Spec
* Runner
* Reporter

With `assertion`, we are able to validate our units. These units come together and define behaviour and eventually create a structure for tests which we named as `spec`. `Runner` is the engine of the system. It collects the specs and executes them. The last part is `reporter`, we use TDD to get feedback as soon as possible, and the reporter provides that feedback.

If we aim to write the simplest test framework, we can easily use assertions built in our language. Node.js' [assert API](https://nodejs.org/api/assert.html), provides that for us, hence we don't need to add anything. Specs are defined by the users of the framework, where we just need to provide an elegant structure that users can follow. We don't need to struggle with reporter, a simple "3 tests are failed" text can be an output for the reporter, also there are some alternatives like [nyan.cat](https://github.com/dgarlitt/karma-nyan-reporter) if you want to have fun. The hardest part for me was the runner part. At the beginning, it seemed easy, but it was hard to implement the reporter without depending on global variables and context.

I shared my work on [this repository](https://github.com/SengitU/kavun), it's still in progress, but reviews are always welcome.
