---
title: "My auto-committer"
layout: post
categories: productivity
date: 2015-03-25 23:33:00
---

I use [vimwiki][vk] as my _personal source of knowledge_. I plan on sharing it, but first I need to set up a few limits on what I'll share, to avoid posting passwords _again_. And I want to make it pretty.

<blockquote>
<p>Pretty things always sell more.</p>
<footer><cite>Albert Camps</cite></footer>
</blockquote>

I use [git][git] to keep my files synchronised, but since I like to have the same source of knowledge both at home **and** at work, I want to have it always in the same and latest version.

I've found that the best way of keeping things synchronised is with a `cron job`, and a _bash script_ that commits new content every hour.

To invoke the crontab editor you need to run:

```bash
$ crontab -l
chmod +x /absolute/path/to/autocommitter.sh
```

The second line is just a reminder, since your bash script must have execution rights, or otherwise it will be useless.

```bash
0	*	*	*	*	/absolute/path/to/autocommitter.sh
```

I first started with only doing this for my [vimwiki][vk], but since currently I am working every day on [my blog](http://www.albertcamps.io) I extended  the script to work with functions, **avoiding code duplication**. I'm such a _good_ programmer.

{% gist 82e5573b1566c6b98ded %}

I will comment on a later post, the relevant information I found in order to write this, and other, scripts I use in my day-to-day activity.

What scripts do you use on a regular basis? Let me know!

[vk]: https://github.com/vimwiki/vimwiki
[git]: http://www.git-scm.com