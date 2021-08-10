---
title: My Personal Rules of Thumb
slug: "my-personal-rules-of-thumb"
tags: ["Software"]
date: 2021-08-10
---

# My Personal Rules of Thumb

I've realised recently I've been engaging discussions related to the web development too often. They're generally involved around fundemantal, but neglected topics. To me;

## *Semantic HTML conveys meaning*

I can not emphasize this enough. In multiple occasions I've observed that semantics simply neglected, because a div tag will also be rendered. Often times in applications that are login gated(where SEO is not applicable), I've seen people just utilising `div`s instead of `form`, `img`, `section` tags and many more I've already forgotten. 
First of all, certain HTML tags has their own functionality out of the box.

- A form will send request a when provided with necessary attributes
- A form will trigger onSubmit event, when an input within the form fires a keypress_enter event.

By using div instead of a form, we literally opt-out from the features provided by the platform and we decide to implement them for ourselves.
For container that contains a heading text alongside with a descriptive content, section tag should be used. Even though render result will be the same, by conveying proper tags, we could easily provide content that is easily readable by the screen readers.
div doesn't accept an alt attribute, unfortunately, your images that are rendered as divs, convey no meaning for people who has visual disabilities and their screen reader will not inform them by reading the alt text. Why you ask? Because div has no alt.
`SEO` is NOT the only reason to write semantically correct HTML.


## Network requests are necessary evil

When an implementation is required for a network request(for anything actually), always think about the failure first. Everybody will implement the happy path and generally speaking, important bugs will not appear within the happy paths. Network requests per se are not evil, we always need a way to communicate with services. What makes them evil is happy path oriented development. Of course this is less of a problem nowadays with proper linter rules, still I observe this problem way too often than I expect.

## Communication is the key of a successfull team

When communicating issues, tasks, asking for help, or during the code reviews. We should always remember that we have our own context and individual we are speaking have their own context. When explaninng, presenting, it's important to get everyone on the same page first by providing necessary information. The other important element is to listen. I know this might feel funny, but I've seen many features implemented poorly because either people don't actively listen to each other, or they do not have enough context. Always share the necessary information and always listen.

## You are not your code

Every comment on a pull request are towards the code, but not towards ones ability to write code. Most of the time, reviews are there to avoid issues or to align the code with the team's standarts. Individual that writes the review, spent time to get some context, understand the code and provide a feedback. Receiving feedback about your work alone is priceless and I personally appreciate working in an industry where I can get fast and accurate feedback.

## Test your assumption (It's a shame this is the last bullet point, isn't it?)

Straight up I'd like to say write tests for everything, but I know it's not always possible. Be honest with yourself and write tests where they add value to the system. Avoid worshipping coverage rules, but try to enhance quality of what's tested. Even if you're not applying TDD (Test Driven Development), you should still have an idea about what to expect when you add that line of code. That might be a div that turns into red with your code, or it might be a console statement that returns the value you expected. The point is, have the expectation first and **do not let the code drive you**.