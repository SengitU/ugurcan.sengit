---
title: "Communication via Git: Part 1"
slug: "communication-via-git-part-1"
tags: ["Git", "communication", "Apprenticeship"]
date: 2018-04-19
---

Software is a living thing. It requires care, you need to continuously improve it every day, like caring a flower. You need to clean it from its bugs, you need to freshen up its soil. Also in software, you need to clear your code from bugs, and you need to add value constantly by `leaving the camp ground cleaner than you find it`.

Maintainability is important, companies invest into software to use and improve it for years. On the other hand, software projects tend to grow so fast, in a fresh project, you will have hundreds of commits within the first 6 months. In such a huge codebase, how can we communicate with the former colleagues to ask the impact of a change? How can we answer questions from the future? We could have achieved that if we had a journal to track the changes. Fortunately, we have something better than journal, we have `git`.

With each commit, we contribute to the life-cycle of the project. It's our responsibility to explain our changes to the future contributors, to make the project more maintainable. We have such a powerful tool, but to make it worth, we need to use it right.

### Commit Messages

Commit messages should be able to answer what is changed. If the change needs further explanation, it should also be in the commit message. Commit messages should not explain `how` the change is made, it's code's responsibility.

General structure for a commit message starts with a title. The title should be able to explain commit briefly and should not be longer than 50 characters. If the title is longer than 72 characters, git will truncate it with ellipsis, so 72 characters is the hard limit. If you can't describe your commit in 50 characters, you might be commiting too much. To create atomic commits, create sub-problems from your main problem and commit these problems.

After the title, if we need to describe the commit further, we need to add a description. Title and description should be seperated by a blank line in order to increase readability. Following commit is from Bitcoin Core, and it's a great example;

```git
commit eb0b56b19017ab5c16c745e6da39c53126924ed6
Author: Pieter Wuille <pieter.wuille@gmail.com>
Date:   Fri Aug 1 22:57:55 2014 +0200

   Simplify serialize.h's exception handling

   Remove the 'state' and 'exceptmask' from serialize.h's stream
   implementations, as well as related methods.

   As exceptmask always included 'failbit', and setstate was always
   called with bits = failbit, all it did was immediately raise an
   exception. Get rid of those variables, and replace the setstate
   with direct exception throwing (which also removes some dead
   code).

   As a result, good() is never reached after a failure (there are
   only 2 calls, one of which is in tests), and can just be replaced
   by !eof().

   fail(), clear(n) and exceptions() are just never called. Delete
   them.
```

If you plan to add just a title to a commit `git commit -m 'Add message here'` will be able to help you, but if you intent to write more `git commit` will prompt your deafult git editor to help you further.

Unlike the title, description will not be truncated by git, but the limit should be 72 character for a single line, to increase its readability. `Vim` added a feature to automatically wrap the lines which have more than 72 characters in the commit messages.

Another aspect, which I've been doing wrong for years, is the mood of the message. Titles should be written with imperative mood, like giving instructions to git. There is an easy way to test your title. Your commit message should always be able to complete the following sentence;

`If applied, this commit will <your message here>`

like;

`If applied, this commit will remove external dependencies`.

Also remember to start with a capital letter and don't add a dot at the end of the sentence. Example above should be committed like;

`git commit -m 'Remove external dependencies'`

Titles of the messages are the bottleneck, hence, we should not add external id's in there. A commit message includes `[JIRA-1905]` will instantly allocate your 9 precious characters. Also, a commit message should not redirect a developer, but **a commit message should be able to describe itself without any third party tool**. We should avoid commit messages with just issue id's. On the other hand, during the project's life-cycle, company could decide to change 3rd party solution and these id's would become obsolete.

_PS: This post inspired by these [posts](https://trello.com/c/iZ3U51XI/94-what-makes-a-good-commit-history)_
