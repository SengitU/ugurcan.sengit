---
title: "Webpack Meets React Meetup"
slug: "webpack-meets-react-meetup"
tags: ["Meetup", "React", "Webpack", "apprenticeship"]
date: 2018-05-09
---

Munich is a great city for a software crafter. Especially for Javascript, one can easily find an interesting meetup to attend every week. Companies are eager to provide space, food and beverages, but most importantly, there are so many kindred spirits¹ who are willing to organize these meetups.

I've been in [Webpack meets React](https://www.meetup.com/webpack-munich/events/249897526/) meetup recently. We had great time with the Webpack's core team([Tobias](https://twitter.com/wSokra), [Juho](https://twitter.com/bebraw), [Johannes](https://twitter.com/Jhnnns)) and [Benedikt](https://twitter.com/bmeurer) from v8 team. Meetup started with Benedikt's lightning talk about `Odd Parts of Javascript`. There is no better icebreaker than making fun of the language we are using every day. How odd was it? See the ones I still remember;

```js
let a = 016;
console.log(a); // prints 14

a = 017;
console.log(a); // prints 15

a = 018;
console.log(a); // prints 18
```

It feels like there is a pattern, until we reach `018`. One more;

```js
const b = 0 / 0; // It will not throw an exception, will return NaN instead

b === b; // false
b === !b; //false
```

Of course, it's because of the [behaviour of NaN](https://stackoverflow.com/a/23666623/1400515), but it doesn't make it less funny.

After Benedikt's great ice breaker session, we had a Q&A session with the Webpack Core Team. We had various questions about both open source and the Webpack itself. These questions helped to build an understanding for the environment which Webpack built on and most importantly, its roadmap.

Johannes presented a hands-on coding session about universal web applications. Together, we've discovered the problems, hence we understood the trade-offs. With Juho's presentation, we've analysed the modern front-end architecture of React Finland web site.

Tobias had a challenging application to build on his presentation, a module bundler! It was quite an experience to understand core bundling steps of webpack. He created a dependency graph, generated a code to provide this dependencies from the graph and removed duplications. It was fascinating to understand simplicity of module bundling, I will add the record for the session as soon as I get it.

As I said, Munich hosts a great community filled with javascript professionals. I can't wait to pair with these professionals on the [JSCodeRetreat #13 - Tetris Edition](https://www.meetup.com/JavaScript-CodeRetreat/events/249843171/) this Saturday(12.05.2018)!

¹: Apprenticeship Patterns, page 64
