---
title: "Way to Refactor"
slug: "way-to-refactor"
tags: ["javascript", "refactor", "apprenticeship"]
date: 2018-05-29
---

My enormous headache didn't let me to write for couple days, but I am back with a great topic today!

I've needed to introduce a feature to the web service in my project. The feature aimed to change a static query to a dynamic one, by the help of the parameter that I get from the user.

There were so many places to change. You can never trust the variable you get from the user, I've needed to introduce validation to prevent the injection. My query was static, to make it dynamic, I've needed to introduce a query builder. Integration that query builder with the system itself. It seemed like a really small task at first, but after I realized that my code wasn't ready for the change. Then [Wolfram](https://twitter.com/wolframkriesing) shared a great tweet with me;

<blockquote class="twitter-tweet tw-align-center" data-lang="en"><p lang="en" dir="ltr">for each desired change, make the change easy (warning: this may be hard), then make the easy change</p>&mdash; Kent Beck (@KentBeck) <a href="https://twitter.com/KentBeck/status/250733358307500032?ref_src=twsrc%5Etfw">September 25, 2012</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

I've needed to make the change easy first. To make the change easy, I started to refactor my code. When you are protected by the unit tests, refactoring is extremely fun to do. At first, I had a module that provides static strings as follows;

```js
const someQuery = `... DATE_ADD('day', -30, CURRENT_DATE) ...`;
```

Since I wanted it to be dynamic, I made it a function;

```js
const someQuery = () => `... DATE_ADD('day', -30, CURRENT_DATE) ...`;
```

My tests failed since I broke the contract. I've updated necessary modules, because I had my tests to point fingers. I was ready to take another step when everything was green again. I wanted -30 to be dynamic, so I made it dynamic;

```js
const someQuery = (interval = "-30") => `... DATE_ADD('day', ${interval}, CURRENT_DATE) ...`;
```

I run my tests again and I was still green. These little steps made my query dynamic. Meantime, I've always been protected with my unit tests.

After making my query dynamic, it was time to the move web service layer. It is extremely easy to get query parameters if you use express. I only needed to pass the parameter which I get from user to my query. I made the change easy, then I only needed to make the easy change. Do you know what happened afterwards? Turned out I also needed to have dynamic `CURRENT_DATE`. Since I've already made the change easy, it took only minutes to introduce the new parameter.

It's important to know your code's capabilities, by that way, you will be able to understand what you need to change to introduce a new feature. If you do the proper refactoring beforehand, the new feature will feel like a small an elegant touch to your code.
