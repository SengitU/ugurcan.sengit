---
title: "Javascript The Language Meetup"
slug: "javascript-the-language-meetup"
tags: ["Meetup", "Munich","Javascript", "Apprenticeship"]
date: 2018-03-23
---

Munich is filled with professionals that care for their craft. One can easily find a meetup about machine learning, TDD, front-end technologies, or with any other topic almost every day.

I attended a meetup with [Javascript The Language](https://www.meetup.com/JavaScript-The-Language/) group yesterday. The main topic was functions in Javascript. We listed concepts that related to functions in javascript and ended up with a huge list. Then we voted and decided to practice `Function` constructor.

I knew that function constructor exists in Javascript, but I have never used it. We wrote a test case and tried to assert that case with our expectation. Very first test cases were so small and predictable.

We expected to have a string inside of the constructor executed.

```js
it("should execute string", () => {
  const returns1 = new Function("return 1");
  assert.equal(returns1(), 1);
});
```

We expected to define parameters for the function by passing their names as arguments to the constructor, and we learnt that the implementation must be the last argument.

```js
it("should add", () => {
  const add = new Function("x", "y", "return x + y");
  assert.equal(add(1, 2), 3);
});
```

We expected to bind context to the created function, and it worked.

```js
it("should return bound x", () => {
  const returnX = new Function("return this.x");
  const returnBoundX = returnX.bind({ x: 1 });
  assert.equal(returnBoundX(), 1);
  assert.equal(returnX(), undefined);
});
```

After binding the function for the second time, we have realized that you cannot override an already bound value.

```js
it("should return first bound x", () => {
  const returnX = new Function("return this.x");
  const returnBoundX = returnX.bind({ x: 1 });
  const returnBoundY = returnBoundX.bind({ x: 2 });

  assert.equal(returnBoundY(), 1); //not 2
  assert.equal(returnBoundX(), 1);
  assert.equal(returnX(), undefined);
});
```

After analyzing this behavior, I think I found the reason. At the above example, when we first bind the scope, we create a closure for x. On the second bind attempt, we also create a closure, but `this.x` will always be closer to the first bound context.

It is a creative activity to fiddle around the concepts we use all the time. We gain more insights about the language by this way. That is how Javascript The Language meetups works so far actually, learning the concepts of language in a framework agnostic way.
