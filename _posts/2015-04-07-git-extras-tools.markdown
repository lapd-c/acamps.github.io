---
layout: post
title: "Git-extras Tools"
date: 2015-04-08T01:52:50+02:00
categories: tools git
---

From time to time, there are sets of tools that are worth checking. [Git extras][ge] is on of this sets of tools.

{% highlight bash %}
$ brew install git-extras
{% endhighlight %}

Besides this, if you use [oh-my-zsh][omz], there's a plugin for git-extras autocomplete too, to help you out.

I will update my previous post about [releases][releases] using the alias from this.

A few of the most interesting are:

* `git ignore` - Adds directly to gitignore, or lists the git ignored files of the folder.
* `git changelog` - Generates a Summary with all the commits
* `git delta` - Lists files that are different from another branch.

<blockquotes>
<p>Doing the same using different tools builds mastery.</p>
<footer><cite>Albert Camps</cite></footer>
</blockquote>

Share with me the tools you use! I would love to learn more.

[ge]: https://github.com/tj/git-extras
[omz]: https://github.com/robbyrussell/oh-my-zsh
[releases]: http://www.albertcamps.io/git/github/2015/04/02/generate-release-notes-for-github.html
