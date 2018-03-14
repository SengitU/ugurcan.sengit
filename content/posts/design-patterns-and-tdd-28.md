---
title: "Design Patterns and TDD"
slug: "design-patterns-and-tdd"
tags: ["DesignPatterns", "TDD", "Apprenticeship"]
date: 2018-03-14
---

Lately I read a lot, wrote a lot about TDD. I practiced a lot with TDD. During this time, I thought about the relation of design patterns with TDD.

I am not an authority to talk about design patterns, but I used them much enough to share my experience. I usually draw blocks which represents objects of the system, lines to visualize their relations and arrows for dependencies. Then the brainstorming starts. With my team, we try to predict which part of the blocks could change in the future, then we apply abstractions to these layers, almost every abstraction problem, there is a design pattern to help.

Creating an upfront design without writing a single test case cripples our minds. Forces us to stick on a design even if it's not exactly correct. Also in the brainstorming phase, I usually fight with imaginary abstraction issues which I would never come across along the project.

On the other hand, TDD aims to write exact amount of code to achieve what you have on your plate right now. Of course, you can see obvious things that could change in the future and apply abstractions in there, but TDD does not aim to write `future-proof` code.

I couldn't find place to fit design patterns to TDD with the way I used design patterns. After some discussions with my colleagues, I think we should clearly see the necessary abstractions and the design patterns we should use at the refactoring step of TDD cycle, instead of deciding which one to use beforehand.

_PS: Rest in Peace Stephen Hawking_
