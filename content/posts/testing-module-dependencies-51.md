---
title: "Testing Module Dependencies"
slug: "testing-module-dependencies"
tags: ["node", "javascript", "dependencyInjection", "Apprenticeship"]
date: 2018-04-16
---

I've been searching for an elegant way to inject module dependencies in nodejs. I need to inject dependencies mostly for testing, and test frameworks usually have their dependency injection approach. Even though I admit that it's overkill for a small sized project, I've been using jest for a while. It also has its own dependency injection solutions.

Assume that, you have following module;

```js
const fancyLogger = require('../utils/fancy-logger');

const reporter = () => {
  ...
  const log = (description) => fancyLogger.log(description);
  ...
  return {
    ...
    log,
    ...
  }
};

module.exports = reporter;
```

In order to test that simple `log` function, we need to inject `fancyLoggerMock`, hence we would be able to check if its log function called or not. To inject dependency in jest, we need to apply four steps;

* Create `__mock__` directory sibling to module you want to inject
* Create a file named exactly same, `fancy-logger` in this case, inside the mock directory
* Write your mock implementation inside of that file (or just return a simple mock and change it according to test's needs)
* Require original file path, and mock original code path(`jest.mock(path)`) inside of your test

This is too much. Meanwhile this approach bloats your file structure, it's also easy to forget some of the steps. Instead of injecting dependency via some framework magic, we should consider writing our code loosely coupled. For this purpose, I would suggest two approaches.

I already mentioned the first approach at one of my previous posts. We can re-write following example;

```js
const reporter = (outputDevice) => {
  ...
  const log = (description) => outputDevice.log(description);
  ...
  return {
    ...
    log,
    ...
  }
};

module.exports = reporter;
```

With this approach, `reporter` module does not aware of the output device. Only important thing for the reporter here is the `interface` of the `outputDevice`, fancyLogger is no longer responsibility of reporter. We can create various types of output devices for our needs;

```js
const reporter = require("reporter");
const fancyLogger = require("../utils/fancy-logger");

const consoleReporter = reporter(console); // console as reporter device
const fancyReporter = reporter(fancyLogger); // Another library as reporter device
const testReporter = reporter({
  // Mock function as reporter device
  log: jest.fn()
});
```

Only downside of this approach is that we can't enforce interfaces in javascript. If the `outputDevice` we use does not have `log` function, reporter would crash. We need to define the interface on unit tests, which we can use as documentation in future.

So, we have our composable modules, but who will compose them? That is the integration part, the one who needs to create that business logic, should also decide upon it's specifications. Integration module should require and compose these modules according to project's needs.

I learnt the second approach from a blog post suggested by [Wolfram](https://twitter.com/wolframkriesing), this approach proposes to pass dependencies as parameters, and keep the usual modules as default parameters. If we modify example above according to this approach;

```js
const fancyLogger = require('../utils/fancy-logger');

const reporter = () => {
  ...
  const log = (description, outputDevice = fancyLogger) => outputDevice.log(description);
  ...
  return {
    ...
    log,
    ...
  }
};

module.exports = reporter;
```

If we want to test `log` functionality, we could inject a mock object as parameter, it will use `fancyLogger` unless it's called with something else. I would prefer to use this approach for obvious dependencies that will not likely to change like `filesystem`. Check out [original blog post](http://picostitch.com/blog/2017/03/discover-extract-dependencies/) for more information, what I wrote here is just an introduction compared to it.
