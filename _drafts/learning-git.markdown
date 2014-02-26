---
layout: post
title:  "Learning GIT"
categories: git
---
Even this article name is _Learning GIT_, some previous knowledge of git is supposed. There are [other resources][git-book] that can be usefull to learn from 0, and understand version control concepts that you might not be familiar with.

Again and again I try to remember some basic uses of git, like creating a branch, and changing to it. So creating this cheatsheet should help me, and only me, because out there you can find awesome tutorials like [this one][git-book].

&nbsp;
- __Change to a new branch called TESTBRANCH__
{% highlight bash %}
$ git checkout -b TESTBRANCH
{% endhighlight %}
&nbsp;
- __Then we change from our new branch back to our previous branch (let's supose it was master)__
{% highlight bash %}
#We first list available branches
$ git branch
$ git checkout master
{% endhighlight %}
&nbsp;
- __Or if we want to publish this new branch__
{% highlight bash %}
#We need to be currently in the branch we are pushing.
$ git push -u origin TESTBRANCH
{% endhighlight %}
&nbsp;
- __We have a remote branch that we want to download to our local:__
{% highlight bash %}
$ git remote show origin
$ git checkout --track -b local_name origin/remote_branch
{% endhighlight %}
&nbsp;
- __Variables worth considering configuring__
{% highlight bash %}
$ git config --global user.name "Albert Camps"
$ git config --global user.email hello@albertcamps.io
$ git config --global core.editor vim
$ git config --global merge.tool vimdiff
$ git config --global color.ui true
{% endhighlight %}
&nbsp;
- __Alias and other useful git commands__
{% highlight bash %}
alias ga="git add -a"
alias gm="git commit -m"
alias gs="git status"
alias gp="git push"
alias gf="git fetch"
alias gl="git log"
{% endhighlight %}
<br />
[git-book]: http://git-scm.com/book
