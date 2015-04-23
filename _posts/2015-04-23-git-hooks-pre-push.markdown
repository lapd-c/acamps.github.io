---
layout: post
title: "Git Hooks. The pre-push hook."
date: 2015-04-23T20:19:03+02:00
categories: git
tags: [git, hooks, scripts]
---

On Tuesday I was talking about [git hooks][ghooks], and how interesting they were. Below you can find my pre-push script for a few simple checks.

As promised, the code:

{% gist 2b3a9b08c0655eb99e28 %}

Don't let the _Gist_ fool you, the file should be named **pre-push** and it should be placed on `.git/hooks/` inside your repositorie **with _execution_ rights**.

This is a rather simple approach, but it can be used as a guide to accomplish something different. It checks for something I consider interesting and doesn't allow pushes if the condition is not satisfied.

Obviously you can push anyway. Here's how:

{% highlight bash %}
$ git push --no-verify
{% endhighlight %}

<blockquote><p>Never forget the knowledge embedded in <b>man</b> pages.</p><footer><cite>Albert Camps</cite></footer></blockquote>

What would you recommend as some other improvement? What would you have as a **pre-push** hook?

[ghooks]: http://www.albertcamps.io/git/2015/04/21/git-hooks-introduction.html
