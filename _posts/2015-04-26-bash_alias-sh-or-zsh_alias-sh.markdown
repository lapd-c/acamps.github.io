---
layout: post
title: "bash_alias or zsh_alias"
date: 2015-04-26T23:53:29+02:00
categories: scripts, terminal
tags: [scripts, terminal]
---

When you spend _enough time_ infront of a machine, and you get tired of doing the same things over and over, you begin to think more on **scripts** and **alias**.

Today I will talk about **alias**, and where to place them.

If you usually do a command, they will usually take a few words. Even if it is something as simple as `wc -l`. The idea behind the alias is to simply write less, so you can spend **more time thinking** than typing.

<blockquote><p>Don't waste your time typing when you can be thinking. The more time you have left for thinking, the more you will excel at your job.</p><footer><cite>Albert Camps</cite></footer></blockquote>

In this scenario adding to your `.bashrc` a line that contains:

{% highlight bash %}
alias nl="wc -l"
{% endhighlight %}

Will enable you to use `nl <filename>` each time you want to know the numer of files of file.

## The short line

But editing the file each time... if it is for small improvements, you might end up without adding any of the aliases ever.

That's why I use:

{% highlight bash %}
echo "alias whatever=\"command I want to add\"" >> ~/.bashrc
{% endhighlight %}

Not precisely, because I use [zsh][zsh] so the file to modify is `.zshrc`. And after this, I need to run:

{% highlight bash %}
source ~/.bashrc
{% endhighlight %}

But in less than a minute, and without editing any file, I just have my new alias ready for action.

## The command

[Unix][unix] comes with a command called `alias` that you can use out of the box to modify your `.bash_alias` file. I don't know how that works if you are using [zsh][zsh]. Hopefully not that terrible.

You can simply list all the alias you have defined by using the command's name, or you can list only one using `alias alias-name`.

It is an interesting way of managing your alias that I haven't used, but can be easier than **my short line**. _But it's not mine_.

## The privacy

Aliases sometimes might be very environment-specific, or might contain sensitive information. I recommend having your aliases in different locations.

A `.zsh_alias` or `.bash_alias` file on your **HOME** directory and then a reference to `source`.

If you want to take it an step further you can have inside your `.zsh_alias` something like:

{% highlight bash %}
source ~/.alias/.zsh_work_alias
source ~/.alias/.zsh_git_alias
source ~/.alias/.zsh_favorite_diretories
{% endhighlight %}

And on those files all the aliases you might need.

I use quite a lot of aliases to avoid typing paths to my repositories and to avoid typing common git actions. What do you use aliases for?

[zsh]: http://www.zsh.org/
[unix]: http://www.unix.org/
