---
title: "Back to Basics"
slug: "back-to-basics"
tags: ["javascript", "date", "apprenticeship"]
date: 2018-05-22
---

Have you ever done date calculations in Javascript without using any external library? I've done couple times, but I've never struggled as much as I do today. Even though I had hard time with Javascript's internal Date API, I would implement it by myself again. I don't want to import a complete date library to handle my basic operations. Nevertheless, you should be careful while doing so.

I need to write a function in order to calculate how many times an individual day occurred during the given year. After acquiring result, let's say **23rd Sunday** of year 2018, I need to find exact date for **23rd Sunday** of the previous year. Even though I had two distinguished tasks, they are still too big to complete within hours. I decided to create a roadmap to achieve my goal.

Firstly, I would like to calculate when does first week of the year starts. Each year, first week starts with the first Monday. Then, I need to figure out how many days passed in this individual year. Following formula will yield number of the weeks passed in that year;

```js
const numberOfWeeks = (daysPassed - firstMondayOfYear) / 7;
```

Sounds like a plan! But, finding first Monday of the year took longer than I've expected. Following code snippet did the trick;

```js
const getFirstMondayOfYear = (year) => {
  const firstDayOfYear = new Date(year, 0, 1);
  const dayOfWeekForFirstDay = firstDayOfYear.getDay();
  const daysUntilNextMonday = (MONDAY - dayOfWeekForFirstDay + 7) % 7;
  return 1 + daysUntilNextMonday;
}
```

`getDay` method in Javascript, returns day of the week. Return value varies between 0 and 6. 0 is Sunday and 6 is Saturday. On the other hand, `getDate` method returns day of the month. Intellisense had suggestions for me when I wrote `.getD`, I carelessly accepted, and for the next two hours, I tried to figure out why my code doesn't work. Last two years, I wrote my code without intellisense and today, I will remove intellisense from my text editor. I am not saying that intellisense is a bad thing, but typing is never a bottleneck, to keep 100% control on my code, I decided not to use it anymore.