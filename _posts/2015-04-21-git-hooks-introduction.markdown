---
layout: post
title: "Git Hooks - Introduction"
date: 2015-04-21T21:09:24+02:00
categories: git
tags: [git, scripts]
---

A very interesting feature that git offers out of the box that you might not have heard of are the quite unknown **[git hooks][git-hooks]**.

A **git hook** is conceptually very easy. It is a **script** that executes before, when or after a certain _git-event_ happens.

If you check in one of your local repositories `.git` you'll see a `hooks` folder that contains:

{% highlight bash %}
hooks/
| applypatch-msg.sample*
| commit-msg.sample*
| post-update.sample*
| pre-applypatch.sample*
| pre-commit.sample*
| pre-rebase.sample*
| prepare-commit-msg.sample*
| update.sample*
{% endhighlight %}

Each one of this scripts does not execute by default. If you want this scripts to execute when the _git-events_ do happen, you should remove the `.sample` extension and give execution rights. I am not using them, and I have no idea of what they do.

And there are a few _git-events_ not included in the previous list. The most interesting  are **pre-push** and **post-merge**. I have a pre-push hook that I will share with you after I can fix a small issue.

<blockquote><p>Don't be stupid and auto-check all the things you always forget before delivering your code. Do so, so you can deliver relaxed. Be a pro.</p><footer><cite>Albert Camps</cite></footer></blockquote>

Did you know about git-hooks? Let me see what you can do with them!

[git-hooks]: http://git-scm.com/book/es/v2/Customizing-Git-Git-Hooks
