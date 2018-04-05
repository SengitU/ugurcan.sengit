---
title: "Cambrian Explosion in Javascript"
slug: "cambrian-explosion-in-javascript"
tags: ["Javascript", "Frameworks", "Apprenticeship"]
date: 2018-04-04
---

We are surrounded by frameworks that makes our lives easier. Especially in the Javascript community for the last ten years, it's like Cambrian Explosion. We have so many libraries, dependencies, that is enough to convert our `node_modules` from folder to a black hole. Major libraries have their own sub-environment to provide solutions. For example, we have `React`, and there is `Redux` for global state management, and there is `react-redux` to connect this two solutions. There are also sub-solutions for the solutions above like `react-redux-form`. So, each major solution creates a new environment and the number of frameworks grows exponentially.

It might seem like I am complaining, but I am not. I feel lucky to be inspired by the talents around the world. I am grateful to everyone who contributes this enriched environment. I don't think any other industry shares as much as software developers share. On the other hand, how can we survive in this environment? How can we find what exactly suits our project?

<blockquote class="twitter-tweet tw-align-center" data-lang="en"><p lang="en" dir="ltr">Using webpack for my &quot;hello world&quot; app <a href="https://t.co/MmnXTl0ebw">pic.twitter.com/MmnXTl0ebw</a></p>&mdash; Tomasz Łakomy ⚛ (@tlakomy) <a href="https://twitter.com/tlakomy/status/965864291500019712?ref_src=twsrc%5Etfw">February 20, 2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

The tweet above explicitly mentions `webpack`, but also applicable for `react`, `jest` or any other framework we use every day. We don't need to deal with webpack configuration for a simple pet project. We could prefer `mocha` -or even more lightweight one- over `jest` if we don't need any mocking feature. Frameworks try to solve everyone's problem, they try to provide additional features to attract people, but do we need them? The more we use, the more we deal with performance issues and the bundle size.

As in every aspect of engineering, here comes the trade-off. We need to be responsible for our project. We need to answer questions like `Why do I need this framework?`, `What is the learning curve?`, `Is there any lightweight alternative?`, `What burden do I get other than what I need?`. I especially used word burden, because the feature that you don't use or need, is a burden for the project.

We always need the use the simplest thing which provides our exact -or close enough- needs, nothing more.
