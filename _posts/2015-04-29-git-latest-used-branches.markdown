---
layout: post
title: "Git - Latest Used Branches"
date: 2015-04-29T23:48:25+02:00
categories: git
tags: [git]
---

Sometimes, while we are working in our branch we have to change to another group of branches to check some things. Some of those times you don't remember which was the name of the branch you were working on. The following commands, helps you find them.

{% highlight bash %}
$ git for-each-ref --sort=-committerdate refs/heads/ --format='%(committerdate:short) %(authorname) %(refname:short)'
{% endhighlight %}

I found this piece of advice at [this conversation](http://stackoverflow.com/questions/5188320/how-can-i-get-a-list-of-git-branches-ordered-by-most-recent-commit), where you can find a few more interesting options. Some with shiny colors.

<blockquote><p>Become a terminal-ninja. It will ease your life in ways you can't imagine.</p><footer><cite>Albert Camps</cite></footer></blockquote>

Usually, when we work at [Social Point][sp], we work in our _private_ branches. Then, when we are done we create a **pull request** on [Github][gh]. After the code is checked, and accepted it is merged on **develop**.

In the whole process of preparing _releases_, once everything is on **develop**, you might forget the name of the branch you were working on. This is when this command comes handy.

Using this name, we can create an alias for easier future use:

{% highlight bash %}
git alias last "for-each-ref --sort=-committerdate refs/heads/ --format='%(committerdate:short) %(authorname) %(refname:short)'"
{% endhighlight %}

What do you use to manage this things in git? Do you use _gitk_ or Sourcetree?

[sp]: http://www.socialpoint.es
[gh]: http://www.github.com
