---
title: "ES6 Modules in Browser"
slug: "es6-modules-in-browser"
tags: ["javascript", "es6", "modules", "apprenticeship"]
date: 2018-06-01
---

For a cool dashboard application, I am using `module` type script loading. It's a cool new feature and it offers a lot. This newly introduced feature, let's you to import your ES6 modules directly. First of all, you don't need to use any kind of bundler. On the other hand, since my scope is the only modern browsers, I don't need to transpile my code. This removes my build process completely. You can observe changes as soon as you type them, no pre-process needed. It's feels like the good old days which we can change the file and get the results right away. Also, it's so simple, you just need to define the `type` as `module`;

```html
<script type=module src="./index.js"></script>
```

Is there any catch? Yes, there is. This approach only works with relative paths for now. There are several ways to pass this problem. You can import your dependencies by the help of script tags or you can serve `node_modules` for dependencies. I am sure we will discover a best practice in the future.

Unfortunately, in my opinion it makes the project harder to tests. Since I can't import a method directly like `import a from 'a'`, I've needed to find a way to make my tests run in node environment. It's impossible for node to understand scripts that I've imported via `script` tag in HTML. To overcome this problem, I've needed to wrap global scope and provide necessary dependencies for node and browsers. To do this, I've used the differences between them. Global object in NodeJS named as `global` and in the browsers, it is named as `window`. So, I wrote the following module;

```js
const globalScopeFinder = () => {
  try {
    if (global) {
      return {
        window: {},
        Chartist: {},
        document: {},
        dateFns: require('date-fns')
      };
    }
  } catch (error) {
    return window;
  }
};

export default globalScopeFinder();
```

This code snippet helps me to understand the current environment. In the browser, `if(global)` line throws exception, then it returns `window` object as global scope. In the node environment, it doesn't throw and returns the objects that I need for test purposes. Usage is as follows;

```js
import globalScopeFinder from './global-scope-finder.js';
const { dateFns } = globalScopeFinder;

const getPreviousYear = (date) => dateFns.subWeeks(date, dateFns.getISOWeeksInYear(date));

export default getPreviousYear;
```

Well, this is not a great solution, but this trick made me capable of using the one of the newest features available.