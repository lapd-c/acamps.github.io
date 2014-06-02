---
title: "Mac-OS-X-and-Jekyll"
layout: post
---

In Mac OS X, the bundled ruby version comes handy for some uses, but if we want to install jekyll, for using it as our bloging platform (as I do), some problems might arise.

In my case, it simply won't install the gem. And after solving it twice, now because of some markup issue, some component of jekyll could not update, leaving my with a buggy 1.4.3, that was useless because one of my drafts broke it up.

I tried removing some lines, just in case some character was the responsible of my misfortune, but what finally helped was:

- Install [rvm][rvm], with the one-liner in their webpage.
- Use [rvm][rvm] to download the latest ruby version, at time of writing this article the latest stable was 2.1.2.

{% highlight bash linenu %}
$ rvm install ruby-2.1.2
$ rvm use 2.1.2
{% endhighlight %}

In my case I had to install the [jekyll][jekyll] gem just once again.

{% highlight bash linenu %}
$ gem install jekyll
{% endhighlight %}

If it complains just use:

{% highlight bash linenu %}
$ zsh --login
{% endhighlight %}

To get back inside the shell in a different mode, and then you'll be able to use the `rvm use` command.

[rvm]: http://rvm.io
[jekyll]: http://jekyllrb.com/ 
