---
title: "Practice: Test Framework"
slug: "practice-test-framework"
tags: ["TDD", "Apprenticeship"]
date: 2018-04-11
---

I have almost completed my practice with the [test framework](https://github.com/SengitU/beaverjs). I definitely recommend everyone to practice on this concept. It's more than a practice, it made me question very basic concepts that I use every day.

I've started up with exploring. I didn't wrote strict tests, I directly dove into code with integration-like tests. This approach helped me to figure out how I wanted to build my API. After I realize this, I almost removed everything and started over with a simple test;

```js
const succeedingExecutable = () => assert.equal(1, 1);
assert.equal(true, execute(succeedingExecutable));
```

Added some more test cases, for asynchronous executables and failing cases and I come up with a simple executor;

```js
const execute = async executable => {
  try {
    await executable.apply();
    return true;
  } catch ({ actual, expected }) {
    return { actual, expected };
  }
};
```

I've added simple method to collect specs and units. Since I knew what I would like to end up with, I started to separate modules that will integrate in future. I split every possible responsibility, at some point, I had modules consist of two lines of code. But, this is not a problem, as long as it increases testability.

I created a reporter to report results and steps. My plan was to use `console.log` for reporting, but I figured out `console` creates a global dependency which makes it harder to test. After thinking a little more, I decided to make my reporter interface composable with any output device with the `log` method.

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

This approach helped me to inject my mock function as output device and increased testability. I've added a runner module to operate executing and reporting process, a collector to collect tests provided by user, and a file loader to discover test files. Even though they didn't integrate magically, after dealing with some little issues, I had my test framework up and running.
