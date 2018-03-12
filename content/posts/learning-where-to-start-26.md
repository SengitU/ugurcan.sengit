---
title: "Learning Where to Start"
slug: "learning-where-to-start"
tags: ["TestDrivenDevelopment", "TDD", "Apprenticeship"]
date: 2018-03-12
---

Deciding where to start a project is one of the hardest steps of a software product. Imagine all the things we need to do, the user interface, the database, continuous integration and continuous deployment and so on. But, where to start?

I started a new project from scratch. I know the responsibility of the application, I have the user interface. It's all on me right now, I need to do my best with the code to finalize the project. But, I don't know where to start.

First, I have started with the presentation layer, the user interface. I decided to use Parcel instead of Webpack without knowing if I need to use any build tool at all. I tried to introduce bundle splitting and styled components. I used React. All these steps only took my focus away from what I need to achieve. I made decisions beforehand, but in software development, necessities should drive the project instead of ideas we have upfront.

I removed everything and started over. This time, by the help of my colleague Wolfram, I decided on the achieve simplest thing I could do. I have created a Command Line Interface tool with the expected data format. Next step was reaching the real data. In order to get to the real data, I have tried to write a layer to connect AWS. At this step, I have dealt with imaginary abstraction problems while I try to learn AWS API.

I have tried to implement edges of the project all that time. Database and the user interface are should be plug-ins for the project, that will be shaped over time with the necessities of our core logic.

This time I started over with implementing the business logic first (I can hear you saying "finally"), hopefully, this time I will shape the frameworks with my project's needs.
