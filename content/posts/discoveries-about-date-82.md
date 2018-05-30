---
title: "Discoveries About Date"
slug: "discoveries-about-date"
tags: ["javascript", "date", "apprenticeship"]
date: 2018-05-30
---

There are 365 days and 6 hours in a year. Humanity tried to divide these days into different units, after years of struggle to set a standard, we've decided to define a week as seven days and a month as various number of days. Why would we have various number of days in months? I've never asked this question before, however, this train of thought have been triggered by a feature that I failed to implement for some time now.

If I introduced a unit in my software which acts different against the different contexts, we wouldn't call that a unit. Probably my pull request would be rejected for a better definition. On the other hand, humanity have a unit called `month` and the number of days it contains varies between 28 to 31. Someday if we find a way to communicate with different intelligent life forms, how can we explain this variation?

There is another thing, I've been taught that a year has 52 weeks. Let's do the math together, there are 365 days in a year, forget about the leap year for now. A week consist of 7 days. If you divide 365 by 7, you will end up with 52,143. Which means that a year has 52 weeks **and a day**. It would be because of my ignorance, but I didn't know that some years have 53 weeks because of this 1 day leap. Just to take things a little more extreme, every fourth year has 52 weeks and 2 days, because of the extra leap year. After embracing these facts, I really appreciate people who wrote date libraries.

Why do I write all of these? Because I've needed to implement a utility to calculate the exact date for the first day of the **nth week of the past year**. To achieve this, I've assumed first Monday of the each year as the start of the first week of that year. After some failed test cases, I've find the standard definition for the first week in a year. According to [ISO_8601](https://en.wikipedia.org/wiki/ISO_8601), There are several mutually equivalent and compatible descriptions of week 01:

* the week with the year's first Thursday in it (the formal ISO definition)
* the week with 4 January in it
* the first week with the majority (four or more) of its days in the starting year
* the week starting with the Monday in the period 29 December – 4 January

After I found this standardized definition, I've just decided to use a framework which implements the specifications. By the help of the [date-fns](https://date-fns.org/), I've achieved my goal with a single line of code;

```js
import { getISOWeeksInYear, subWeeks } from "date-fns";

const getPreviousYear = date => subWeeks(date, getISOWeeksInYear(date));
```

By questioning, I've learnt some valuable information about completely different domain today. Even though we have standards keep everyone on the same page, I believe we need to have strict definitions for the time as we have for weight or distance.
