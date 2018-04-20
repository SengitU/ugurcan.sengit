---
title: "Communication via Git: Part 2"
slug: "communication-via-git-part-2"
tags: ["Git", "pullRequest", "Apprenticeship"]
date: 2018-04-20
---

While commits provide solution to minimal problems, pull requests provide a broad solution to bigger problems, by the help of the commits. Even if a structured pull request is important, it cannot be able to provide maintainibility by itself. To learn more about proper commit messages, check out [Communication via Git: Part 1](https://www.sengitu.com/posts/communication-via-git-part-1/).

Pull requests are envoys of our code. They will communicate with the maintainers, with the owners or with the colleagues. It will require some time to be consumed, understood and concluded. Even though some steps of the pull requests could be automatized, a pull request will always require people's time. We either be informative and helpful on the pull requests to make everyone's life easier, or we let them to become time-consuming monsters for the reviewers. This could even make team to question about helpfulness of pull requests.

First of all, pull requests should be as small as possible. Small pull requests require less time to be understood and to be concluded. But, how small it should be? I wouldn't say three or five files, but it should be able to provide functionality with smallest effort possible.

A way to ensure small pull requests is to apply single responsibility principle for pull requests too. Files that changed for the same reason, should be included in the same pull request. Even if you have unrelated commits inside of the pull request, you can always create a new branch and cherry pick the commits that serve the same purpose. This approach will yield smaller, meaningful pull requests. Most importantly, reviewer will not be forced to context switch. If code violates single responsibility and implements let's say three features, two working and well written features will not be shipped because of the 3rd feature which is rejected.

One of the common mistakes is reformatting the code. The reviewer is there to review functionality, and reformatting the code will confuse the diff with the unnecessary lines. If you really need to reformat, it's a good reason for having another pull request.

Needless to say, we should `leave the camp ground cleaner than we find it`. Code should build, tests should pass. We also need to add new test cases to cover the new functionality we brought. We can and we should at least automatize this part. There should be a continuous integration setup to build and run the tests on every pull request. Also having a rule to fail the continuous integration if the code coverage drops under a certain value, will ensure that tests exists in the project. That being said, do not trust coverage report completely, since the bad tests are worse than no test.

Describe the issue with a proper title and description. Link the pull request with the issue if exists. Meaningful commit messages will help you during this part.

In the best case, your code will be accepted and merged into code base 🎊🎊🎊, but in the worst case, you will need to change your code and align with the master. It's reasonable to track changes with rebase, instead of merge, to make the commit history less polluted.

Unstructured pull requests could become disastrous and sticky. It's hard if not impossible to track other changes when your pull request is open for a month and the code base is completely different. We must care for out commit messages and pull requests as we care our code.

_PS: This post inspired by [these](https://trello.com/c/CihwuD6C/222-check-online-materials-for-reviewable-code) posts_
