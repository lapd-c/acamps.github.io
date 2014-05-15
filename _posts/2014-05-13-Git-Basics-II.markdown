---
layout: post
title: "Git Basics II"
date:   2014-05-12 19:40:00
categories: git
---
º
In this follow-up article, a few interesting points of GIT have been highlighted.
 + Create a git remote in some local storage.
 + Merge branches
 + git rm or git add
 + git tag. Adding a tag

- __How to create a git remote__

In the folder you want to place the git remote
cd /folder/you/choose
mkdir folderForGitRemote
cd folderForGitRemote
git init --bare

Then you have a local folder that you want to copy to the remote, but first you have to initialise it as a git repository.
{% highlight bash %}
# Without the --bare option this time
cd /folder/that/contains/your/information
git init
{% endhighlight %}

{% highlight bash %}
git fetch
git remote -v
git remote add name url
{% endhighlight %}
Url in this scenario could even be `file://` element, which makes everything very interesting, and allows to use Dropbox very interestingly.

{% highlight bash %}
git pull origin
{% endhighlight %}
To change the default origin or branch, edit your `.git/config` file
or
{% highlight bash %}
$ git pull -u remote-name 
#(git config https://www.kernel.org/pub/software/scm/git/docs/git-push.html)
{% endhighlight %}
&nbsp;
- __Merge branches__

To merge branches, you first have to jump to the branch you want to update. In this example, we will add the current development in the `development` branch to the `master`.
{% highlight bash %}
$ git branch master
$ git merge develop
{% endhighlight %}
Some problems might arise from the merge if there are conflicts, but we will deal with this in another post.

- __Delete files__

Comments on git rm. If you really need to delete files, sometimes checking this will be interesting.
{% highlight bash %}
$ git rm -rf
$ git rm --cache
$ git add -A
{% endhighlight %}
&nbsp;
- __Tag commits__

Also it is useful to tag some special commits, so you can go back to them when you need, or users can download specific versions while development continues.

To see which tags have been created just:
{% highlight bash %}
$ git tag
{% endhighlight %}

To add a new tag. For this it is interesting to consider semantic versioning.
{% highlight bash %}
$ git tag -a v1.4 -m 'my version 1.4'
{% endhighlight %}

Then you need to push your tags or get them from the remote.

Setting your branch to exactly match the remote branch can be done in two steps:
{% highlight bash %}
git fetch origin
git reset --hard origin/master
{% endhighlight %}

If you want to save your current branch's state before doing this (just in case), you can do:

{% highlight bash %}
git commit -a -m "Saving my work, just in case"
git branch my-saved-work
{% endhighlight %}
