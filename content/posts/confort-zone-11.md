---
title: "Test Driven Development"
slug: "test-driven-development"
tags: ["TestDrivenDevelopment", "TDD", "Apprenticeship"]
date: 2018-02-16
---

A developer must have a way to verify herself, must make sure that she develops the `thing right`. The best way of verification for the code is testing. Testing the code will provide the feedback that a developer needs. If the **behaviour** of the code is wrong, it is defined as a defect. A _bug_ causes this defect. No! Let's admit it, like [JB Rainsberger](https://www.jbrains.ca/) says, it's a _mistake_.

When a mistake occurs development will start again. There will be some rework done, and eventually, the code will be tested again. Even so, there is no way to assure that the code will make it to the production this time. What if we can raise the odds? What if we can decrease the rework?

The best way to be sure the code _behaves_ expectedly, is to test it upfront by defining its behaviour with a simple test. Without any implementation, the test will fail. We implement the exact code to make the test pass. This point forward, we will define a follow-up behaviour, and the test will fail again. We will make it pass and fail over and over again until we achieve the final behaviour.

In our journey to the final behaviour, we will see opportunities to do some refactoring, to apply the best practices. Even after then, requirements of our client may change. In any case, we wrote the `working code that is easy to change`. Now, we got covered by our unit tests and we can make changes while we are confident that our code behaves as expected.

Each code snippet has a destination. By creating a test case, we define a stop between the current point and the destination. Smaller the distance between the stops, the lesser logic we inject the code. Each small step will lead us the way to the well-crafted code while making it easier to return to the previous point if we make a mistake.

### Patience is the key

I know leaving old habits is difficult. At a first glance, hacking your way through the destination might seem easy, but it's not. It costs much more than one can imagine. We might think we see the implementation upfront, but if we let the **code** lead us along the way, we will write the exact amount of code and probably end up with a wiser solution. This is a craft to master, but the results are enlightening.

I will finish with a quote from Kent Beck, `Write tests until fear is transformed into boredom`.