---
title: "Communication via Git: Part 1.1"
slug: "communication-via-git-part-1-1"
tags: ["Git", "communication", "commitMessages", "Apprenticeship"]
date: 2018-04-23
---

After I release my [Communication via Git: Part 1](https://www.sengitu.com/posts/communication-via-git-part-1/), my colleague Wolfram provided valuable feedback for my post;

<blockquote class="twitter-tweet tw-align-center" data-conversation="none" data-lang="en"><p lang="en" dir="ltr">I would like to see more &quot;why&quot; for the things you describe. I know many of them are described as common sense, but why?<br>For example:<br>- 72 chars length<br>- don&#39;t end with a dot<br>- not refer to 3rd party<br>- ...<br>Why?</p>&mdash; Home Officer (@wolframkriesing) <a href="https://twitter.com/wolframkriesing/status/987618967970893825?ref_src=twsrc%5Etfw">April 21, 2018</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

I decided to devote this blog post to trace the answers. Taking another look with Wolfram's tweet in my mind after several days, helped me to realize that I've been too busy to state the ideas. But, apprenticeship itself is for discovering the reasons behind the ideas.

- Commit messages should not explain `how` the change is made, it's code's responsibility.

  - Even though this one is self-explanatory, I wanted to state this one again. Because, in my opinion, this one is as dangerous as comments on the code. Code should be fluent enough to explain itself. Instead of trying to make it clear with commit messages, one should be striving for better code. If someone finds and reads that single commit, she probably seeks for an answer of why question instead of how.

- 50 characters limit on the title and 72 characters limit on the description.

  - I thought this was a common-sense rule for the sake of readability and I didn't know the math behind it. Title limit, 50 characters, is average length of the commit message summaries' in the Linux Kernel. Since the reason behind this one is still objective, every team can set their standard. Be aware, 72 is still hard limit for a summary, git will truncate your message with ellipsis, so don't type further.

  - 72 characters limit made more sense to me. To make the description readable in a 80-column terminal, `git log` adds 4 blank spaces, and to make the message centred, we also add 4 blank space, which yields 72.

- Don't end commit messages with dot.

  - While writing this post, I became even more confused about this rule. People favours this rule, because of the precious one character in the title. But, it doesn't make that much sense for me right now. I didn't expect to see this much discussion around this topic. Correct me if I am wrong, but it seems like we've found yet another topic to argue to the eternity.

- Do not refer to 3rd party issue ids on the commit summaries.

  - There are several reasons for this one. First one is losing your precious characters in the title. Title is already limited with 50 characters, meanwhile issue's usually more than 7-8 characters.

  - People uses `git shortlog` or `git log` to understand problems right away. This is our communication tool, this is what already we have in the first place. Why do we need to introduce an extra step? Also, since we are the ones to deal with the problem, who else can describe the problem better than us.

  - If we need to add an issue id, there is no better place than the description.

- The mood of the message should be imperative.

  - Imperative messages makes sense to me, since we are giving commands to git to change our codebase. For example; Add this commit to the code base and `Increase testability for reporter module`.

Most of the bullet points above depends on the agreement with your team. Changing them are usually harmless as long as you have a standard.

Remember the importance of the commit messages, they aren't that important until they are. When they are important, it would be so hard to track down 6 months in a library without standard.