---
layout: post
title: "Generate Release Notes for Github"
---

[Github][gh] allows to add [releases][release]. This is convenient, but tedious. Below is a way to automate it.

You may add this aliases to your git configuration. [Jesús Canales][jesus] handcrafted them, and handed them to me, as I saw they - [backend people][engineering]- were using something for automatically getting the commits that belonged to a [release][git-flow].

{% highlight bash %}
ri = !f() { git loc `git lt`..develop --no-merges; }; f
loc = log --pretty=format:-(%h)%s
lt = describe --tags --abbrev=0
{% endhighlight %}

Now:

* With `git lt` you'll get the latest tag created
* `git loc` tells you the differences between two pointers
* Finally `git ri` shows the differences between the last created tag, and develop.

Actually, `git ri` **crashes** for me, but I can execute:

{% highlight bash %}
git loc `git lt`..develop --no-merges
{% endhighlight %} sepparatedly

The `--no-merges` flag helps to remove useless commits that only indicate that content was merged.

Now you only need to visit a previous published [--tag][tag] and click on the _Release Notes_ link on the right

All this can be used to generate a script using [Github's API](https://developer.github.com/v3/repos/releases/#create-a-release), which I will do _soon_.

<blockquote>
<p>Do it now. Generate scripts so you don't need to remember anything more than "I have an script for that".</p>
<footer><cite>Albert Camps</cite></footer>
</blockquote>

[gh]: http://www.github.com
[release]: https://help.github.com/articles/creating-releases/
[git-flow]: http://danielkummer.github.io/git-flow-cheatsheet/#release
[jesus]: https://twitter.com/tanque_tm
[engineering]: http://engineering.socialpoint.es
[secret-link]: https://github.com/arzynik/github-auto-release
[secret-link-2]: http://www.barrykooij.com/create-github-releases-via-command-line/
[secret-link-3]: http://www.janosgyerik.com/deploying-new-releases-using-git-and-the-post-receive-hook/

[secret-link-4]: http://stackoverflow.com/questions/9132144/how-can-i-automatically-deploy-my-app-after-a-git-push-github-and-node-js
[secret-link-5]:https://github.com/tj/git-extras/wiki/Commands
