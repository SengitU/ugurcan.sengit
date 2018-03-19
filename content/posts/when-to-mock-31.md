---
title: "When to Mock?"
slug: "when-to-mock"
tags: ["TestDrivenDevelopment", "Mock", "Apprenticeship"]
date: 2018-03-19
---

Test first programming drives us to a better design. Before writing any other code, we are making sure that the module is testable. To make the business logic testable, first we think that logic without any external modules which will use it in future. We test drive the valuable business logic first, then other parties connected to this logic, let's say to store, or to present.

Thinking this way, will move every pluggable modules to the edges of the project, and the business logic will sit in the core.

When it's time to test pluggable modules, I generally use mocking. For example, I needed to mock `athena-client` library's API methods to check if I am calling with the right parameters and the right order, or previously I mocked WebRTC engine to get what I expected.

Today my colleague [Wolfram](https://twitter.com/wolframkriesing) suggested me not to unit-test what I don't own. It didn't make sense for me at first, I would not feel safe if there is no test for calling exact parameters with exact order. He suggested me to use integrated tests instead for that part of the project. If the 3rd party API changes order of the arguments, or method names, mocks will not make tests fail and I will have illusory confidence with my code. But, the integration tests will surely fail. At first, I thought about having both, but it would create duplication since the integration tests will also test exact function and exact order.

What do we need to mock then? According to Eric Elliot, nothing in his article named [Mocking is a Code Smell](https://medium.com/javascript-scene/mocking-is-a-code-smell-944a70c90a6a). There is a [response](https://medium.com/@koresar/about-mocking-is-a-code-smell-a8c0720e04b3) to that post and a huge discussion which is really informative about mocking things.

I still think that, in order to unit test a module, we need to mock dependent modules. When we don't mock, we can't test drive the module. We need to know what do we expect from another module, in order to test variations of our current module's behaviour.
