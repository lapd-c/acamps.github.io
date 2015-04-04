---
title: "Several ways to solve RStudio whitescreen."
date: 2015-04-04 17:00:00
layout: post
categories: rstudio
---

If you encounter yourself fighting agains a **whitescreen** in _RStudio_ this post offers a few solutions that might help to solve it.

I encountered this error while re-installing R with [Homebrew][brew] on my Mac, but I think it can occur under different scenarios.

First of all, I would recommend the _typical_ delete and reinstall RStudio.

If that doesn't work, [resetting RStudio's state][reset] could be helpful too.

However, none of this things helped me make my [RStudio][rstudio] work again.

What did was to remove [RStudio][rstudio]'s **complete** installation.

{% highlight bash %}
$ sudo rm -r /Library/Frameworks/R.framework/
{% endhighlight %}

This should be enough.

As a side note, it helped to find the relevant files activating Linux's `locate` command.

{% highlight bash %}
$ sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.locate.plist
$ locate rstudio
{% endhighlight %}

<blockquote>
<p>Use the `locate` command's awesome powers. But use them wisely.</p>
<footer><cite>Albert Camps</cite></footer>
</blockquote>

I tried the things mentioned [here][sol1], [here][sol2] and [here][sol3].

[sol1]: https://support.rstudio.com/hc/communities/public/questions/200654443-R-studio-starts-with-a-white-screen
[sol2]: https://support.rstudio.com/hc/communities/public/questions/200634108-RStudio-does-not-start-white-screen
[reset]: https://support.rstudio.com/hc/en-us/articles/200534577-Resetting-RStudio-s-State
[sol3]: https://support.rstudio.com/hc/communities/public/questions/203378386-RStudio-white-screen-on-launch-on-OSX-A-Solution
[rstudio]: http://www.rstudio.com/
