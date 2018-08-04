---
title: "Busconf 2018 🚌"
slug: "busconf-2018"
tags: ["Functional Programming", "Busconf", "Unconference"]
date: 2018-08-04
---

Couple hours ago I've left the peaceful environment I've been in for two days. [Seminarzentrum Rückersbach](https://www.holidaycheck.de/hi/seminarzentrum-rueckersbach/11360f57-711c-3fab-bb71-32d039c81bfd) was a great place to have an open space conference. It is isolated from all kind of side effect of the society, which makes it easier to focus and learn.

A couple of days before the conference, I thought if I wanted to host any session and I just didn't want to. My aim was to understand the real-life usage of the purely functional languages and get inspired by the professionals in this area. Well, you can never know what would happen in an unconference. This time I've met with colleagues from Codurance and 8th Light, which are applying the apprenticeship program for years now. We've decided to host a session about the apprenticeship program in our companies.

The apprenticeship program is an interface that implemented by the companies according to their needs. Unfortunately, there are not so many companies applying this pattern, so I would say it is quite new. It was a great opportunity to talk about different implementations of the apprenticeship program. Right now, I have ideas to shape our apprenticeship program a little more.

When I quit my job with the J2EE stack to work in the Javascript environment, the biggest problem I had was to lose the type safety. Back then, it never felt right, for quite some time I tried to understand why we don't bother about the type safety anymore. I usually end up with articles like [You Might Not Need Typescript(or Static Types)](https://medium.com/javascript-scene/you-might-not-need-typescript-or-static-types-aa7cb670a77b). I understand the reasoning behind this type of articles, practices like TDD or code reviews will help you more than the static types. Apparently, the tide has turned. People were talking about the **type safety** all the time. I wonder if this is a hype triggered by the _Typescript_ or finally we have our minds set. Only time will tell.

I knew the concept of the _Maybe_ from my prior studies with Scala _-scala.Either-_, but I've really liked the usage in the PureScript. The hardest part of my studies with Web Components was to make them testable. The problem is, most of the time your web component is highly dependent on the DOM. PureScript abstracts the DOM interface which I assume makes it more testable. However, this is not the only upside. DOM selector returns a _Maybe_ which could yield the real _DOM Object_, or _Nothing_. Since the element wrapped within the _Maybe_, it forces the developer to handle all cases. This is a discipline one can also apply without _Maybe_. You just need to handle every possibility carefully. It's easy to forget or neglect if the language doesn't force you to handle every possible case.

Exhaustiveness check is another great topic that helps you to handle every single case. Check out my [Case Classes In Scala](https://www.sengitu.com/posts/case-classes-in-scala/) post for more information about exhaustiveness check.

After BusConf 2018, I've decided to assess PureScript and TypeScript to feed my need for types. It was a great opportunity to learn for two days without any kind of disturbance.

See you in the [JSCraftCamp](http://jscraftcamp.org/) next week(10-11 August 2018)!
