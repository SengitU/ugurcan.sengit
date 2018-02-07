---
title: "Getting Started with Scala"
slug: "getting-started-with-scala"
tags: ["Scala", "SBT", "Exercism.io", "Kata"]
date: 2018-02-07
---

Let's get our hands a little more dirtier with `Scala`. First of all, I will talk about the hardest part. At least I thought it would be the hardest part. When I start with a brand new language, hardest part for me is always the very first steps. Setting up the environment! 

At my first job, I have used Java. It took a couple of days to set up the environment, even though we have used Ant to manage dependencies. Losing all the excitement of first few days to environment setup was total buzz kill. Modern Javascript is definitely better to be honest. Most of the time a simple `npm i` does the trick. Since Scala runs on top of JVM I was kinda afraid, but thanks to [sbt](https://www.scala-sbt.org/) that wasn't the case. 

`Sbt` is a build tool for Scala with some cool features. You can simply create a new project from command line with a simple command: `sbt new sbt/scala-seed.g8`. The cool thing is, sbt has reasonable amount of project templates for people's needs. Most of the exercises I came across are using this tool which helps a lot for a smooth start to language!

After the environment setup and studying the koans I mentioned yesterday, I was ready to do some katas. I have found out [exercism.io](http://exercism.io/languages/scala/exercises) for my scala katas. I was surprised to find out that exercism.io was even cooler than sbt! It also has a command line interface. By the help of this interface, one can simply get exercises installed to computer with `exercism fetch scala sum-of-multiples` command. After this point, `sbt test` command simply runs the tests according to users implementation. After resolving the kata a simple `exercism submit PATH_TO_FILE` command submits the user's answer. No, it is not over yet! After this point, it creates a space for user to share the solution with community, you can even ask for code review from people easily. This is an example for a resolved kata: [Feel free to share your comments.](http://exercism.io/submissions/e8d6138bf06340c7a54f8cc718da1cd8)

The good thing about katas is that you can practice more than one solution just to achieve the best performance or readability or whatever you need. Tomorrow I plan to write more about that on an example.