---
title: "Javascript Code Retreat #13 - Tetris Edition"
slug: "js-code-retreat-13"
tags: ["Javascript", "CodeRetreat", "jscr13", "apprenticeship"]
date: 2018-05-14
---

Last Saturday, I've attended another great meetup, [Javascript Code Retreat #13 - Tetris Edition](https://www.meetup.com/JavaScript-CodeRetreat/events/249843171/). It was quite an experience to share my Saturday with other Javascript enthusiasts on a well-known problem.

We had a great structure, what we needed to do is pairing with another Javascript enthusiast and try to implement the Tetris game. We didn't need to ship anything, honing our skills was the only purpose, that's why we deleted our code after each session.

Event started with a simple and explanatory presentation by [Wolfram](https://twitter.com/wolframkriesing). He introduced the rules, shared insights about TDD and the four rules of simple design. Also, we had handy little flyers to remind us these insights. We've paired by the help of a little ice breaking session and started hacking!

<blockquote class="twitter-tweet tw-align-center" data-lang="en"><p lang="und" dir="ltr"><a href="https://twitter.com/hashtag/jscr13?src=hash&amp;ref_src=twsrc%5Etfw">#jscr13</a> <a href="https://twitter.com/jsCodeRetreat?ref_src=twsrc%5Etfw">@jsCodeRetreat</a> <a href="https://t.co/Y4Zx0RHLQ5">pic.twitter.com/Y4Zx0RHLQ5</a></p>&mdash; Pın (@pinarkaymaz6) <a href="https://twitter.com/pinarkaymaz6/status/995214304881336320?ref_src=twsrc%5Etfw">May 12, 2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

At the first session, we took our time to examine the Tetris game. We played some Tetris first to understand the game, honestly, I knew the game as I know my initials, but it's fun to play anyway. We've implemented the board, square shape and all of a sudden, we were out of time. In the first session's retrospective, people shared their approaches to the problem. You can't imagine how many different ways exist to represent a simple Tetris board.

The good part of Tetris game is, there are so many little problems to solve. With my pairs during the sessions, we've started from the board, the shapes, the engine provides ticks to the game, and the logic removes the completed lines. Each time we had different implementations and different representations for the concepts. Having different problems on each session kept the excitement level high. As a side effect, I've grasped all of the core parts of Tetris game until the end of the day.

Having different things to implement was not only thing that kept people excited. Wolfram proposed some challenges to make things harder. First challenge was not talking with your pair. You don't need to talk anyway if you are descriptive enough in your code and tests, do you? Well, that's not always the case. After 6 months, even our code is not familiar to us sometimes. It was a great challenge to communicating via code itself.

Other challenge was harder, especially if you are willing to accept the challenges. The challenge was simple at first, `do not use if - switch case`, it felt doable, then he introduced 4 more, the complete list was something like the following;

* No if
* No return statement
* No naked primitives
* No loops
* No assignment

My pair took the challenge to the extreme and we tried to apply all of the rules above. We had to use some freaky workarounds. Honestly, it's impossible to achieve anything without logical operations, so instead of if, we have used `&&` and `||` operators in an extreme way. It was hard to overcome that much challenge, but it was extremely funny because of that.
