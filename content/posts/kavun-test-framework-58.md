---
title: "Kavun: Spec Runner"
slug: "kavun-spec-runner"
tags: ["kavun", "tdd", "javascript", "specRunner", "Apprenticeship"]
date: 2018-04-25
---

During my apprenticeship, I talked about TDD, frameworks and simplicity. After reading `Test Driven Development by Example` book by Kent Beck, I wanted to write my own spec runner. Luckily, apprenticeship is the best place to discover.

During the implementation, I had chance to analyse well-known test frameworks, every one of them has upsides and downsides. But I think, majority of the test frameworks provides too much. I prevented myself and I tried hard to stay within my scope. Since node itself provides an assertion library, I only needed to provide spec runner.

I named my library after my first cat, `kavun`. Kavun does not interfere with your global scope, does not bind or remove anything from the global context. Since its only responsibility is to run the specs, it's fast, faster than I expected. Before I get into the examples, feel free to create issues, provide feedback, create pull request on the [repository](https://github.com/SengitU/kavun).

After installing library by;

`npm i kavun`

Anyone can use it easily by requiring its keywords;

`const { spec, unit } = require('kavun');`

A simple async test case with async/await;

```js
unit('Example async unit with async / await', async () => {
  const actual = () => new Promise(resolve => resolve(true));
  const expected = true;

  const result = await actual();
  assert.equal(expected, result);
});
```

You can also use promises, as long as you remember to return the `Promise`;

```js
unit('Example async unit without async/await', () => {
  const actual = () => new Promise(resolve => resolve(true));
  const expected = true;

  return actual().then(result => assert.equal(expected, result));
});
```

You can use `spec`s to structure your unit tests;

```js
spec('Example Spec', () => {
  unit('unit', () => {
    const expected = 2;
    const actual = 2;
    assert.equal(actual, expected);
  });

  spec('Async', () => {
    unit('with async / await', async () => {
      const actual = () => new Promise(resolve => resolve(true));
      const expected = true;

      const result = await actual();

      assert.equal(expected, result)
    });

    unit('without async/await', () => {
      const actual = () => new Promise(resolve => resolve(true));
      const expected = true;

      return actual().then(result => assert.equal(expected, result));
    });
  });
});
```

One can provide directory to check for tests inside of it. To make it easier to collect, test cases should end with `*.spec.js`. If no directory is provided, `kavun` will try to run specs inside the `tests` folder.

I remember the very first days of my career, spec runners, mock libraries were like magic to me. After implementing my spec runner, I am blessed by the simplicity behind it. I would suggest this experience to every developer. I would like to thank to my colleague [Wolfram](https://twitter.com/wolframkriesing), since he encouraged me to take this path.