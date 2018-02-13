---
title: "Practice: Data Visualization Tool"
slug: "practice-on-data-visualization-tool"
tags: ["react", "create-react-app", "javascript"]
date: 2018-02-12
---

Creating a web application from scratch is the hardest part of development process. There are so many decisions to make like `which build tool should I use?`, `which spec runner should I use?`. I usually find myself suffering while checking library compatibility problems -That was the case for all JS developers couple years ago, check out the JS fatigue-. Today I succeeded to dodge this pitfall by bootstrapping my app with [Create React App](https://github.com/facebook/create-react-app). This repository has single purpose: `Create React apps with no build configuration.` 

By the help of `Create React App`, today I have started my data visualization tool for Trello. My goal was to visualize completed tasks against their categories on the pie chart. I created small steps to follow in my mind:

- Get data from Trello
- Extract the information from this data, namely extract `Done Weekly` or `Done Overall` columns
- Extract labels from each card on the given column
- Adapt data for the visualization framework(`ChartJS in this case`)

Since my table is public, a simple `GET` request to `https://trello.com/b/[boardId].json` address fetched my precious data. Since the list's names were `String`s like `Backlog > Tools`, I have used enum-like objects to prevent typos;

~~~["JavaScript"]
export const listNames = {
  BACKLOG_OTHER: "Backlog > Other",
  BACKLOG_TESTING: "Backlog > Testing",
  .
  .
  .
}
~~~

After this point, I created simple `key-value pair` to keep these listNames with their Ids. In order to create this pair, I needed to initialize class with the board data. I wanted this class to be `singletone` assuming that data will stay the same.
I have overthought and I have failed to write testable code. Test implementations started to have huge `beforeEach` blocks with data initialization. Coupling between modules increased and I have failed to dodge this pitfall. After struggling for an hour, I realized that I am on a mud. I stopped being stubborn and removed whole class, just kept the tests. Eventually, I found another solution I can use for this case.

Every software crafter has been through this problem at some point. Accidently, we start to inject more meaning on a simple class. That simple class gets used by other developers for multiple purposes. At some point, abstraction becomes impossible. We must stop being stubborn and take a break to get rid of tunnel vision.

Being able to realize that I am not going anywhere, saved my day. I have successfully published an alpha version on https://gracious-booth-c323f1.netlify.com/. 