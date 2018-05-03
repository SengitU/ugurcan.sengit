---
title: "Progress Bar with Animate Interface"
slug: "progress-bar-with-animate-interface"
tags: ["animation", "javascript", "Apprenticeship"]
date: 2018-05-02
---

I've never get along with CSS as I do with Javascript. This fact pushed me to dive deeper on Javascript in my first years as a software developer. With this attitude, CSS become the weakest link in my toolbox. I faced this fact and I've tried to get out of my comfort zone since last couple years, but old habits die hard.

One of my tasks for this week is developing a simple progress bar. Implementation might be too obvious for you, but it wasn't for me. Couple times during the weekend, I caught myself thinking about the implementation details.

The implementation which kept my mind busy was quite easy. I just needed to have one parent and one child `div`. `width` property of the child div needed to increase with each tick, starting from 0% to 100% in order to fill whole space. What I couldn't figure out was how to provide ticks to increase this percentages. Right in that moment, my tendency, Javascript, showed up and made things more complicated. I thought about providing 0.5 second duration to each interval to provide a callback which will increase percentage of child div, and which will stop at 30th tick. What I have forgotten was the whole [Animation API](https://developer.mozilla.org/en-US/docs/Web/API/Animation). Thanks for reminding [Wolfram](https://twitter.com/wolframkriesing).

By the help of the `Animation API`, it became extremely easy to provide ticks. Actually, API itself handles the whole process, you just need to provide steps as follows;

```js
element.animate([
    { width: '0%' }, // Starting state
    { width: '100%' }, // Completed state
  ],
  timeInterval // Time between the starting state and the completed state
);
```

As far as I know, Animation API animates by using CSS animations, which makes it even faster. It's crucial to know the exact tools you need to use in order to come up with a proper solution.
