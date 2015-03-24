---
title: "Git - get diffable files from a branch / pull request"
date: 2015-03-23 22:32:33
categories: git
---

I spoke about [git][git] a couple of days ago. Since I use it almost everyday I try to improve my use of it. Kaizen, you know.

Yesterday I discovered from [this remarkable blog][blog] how to **get the diffable files comparing one branch with another**.

```bash
alias get_diffable_files="git diff --name-only --diff-filter=ACMRTUXB origin/develop..."
```
	
As I commented, since we use [git-flow][git-flow], this usually means checking the current work on a **[feature branch][feature]** against **develop**.

----

My next objective in _this subject_ is to enable and **change the default hooks on git**, to check if my new code broke something.

I will use this new alias to also create a small process watch that runs related tests to the code currently being changed. Something similar to **[omnitest][omnitest]**.

<blockquote>
<p>
Achieve a state of peaceful programming <em>Kaizen</em>. If you don't know what Kaizen is, google it, for heaven's sake.
</p>
<footer>
<cite>Albert Camps</cite>
</footer>
</blockquote>

Let me know in the _comments section_ if you find this article **useful**!

[git]: http://www.git-scm.com
[git-flow]: http://nvie.com/posts/a-successful-git-branching-model/
[feature]: http://danielkummer.github.io/git-flow-cheatsheet/#features
[blog]: http://zachholman.com/posts/how-github-writes-blog-posts/
[omnitest]: http://infinitest.github.io