---
layout: post
title: "Github Is Under Attack"
date: 2015-03-30T22:35:46+02:00
---

Friday we found out that [Github][gh] was receiving a [DDoS attack][ddos], but at that point what we didn't know was **why** [Github][gh] was being attacked.

And we forgot about it.

But today, as we got back to work, we discovered that [the attack was still ongoing][attack-tweet], and that it has evolved.

I'm no journalist, so I will keep it simple.

It looks like _**someone**_ is attacking a couple of projects hosted in [Github][gh] - that are about mitigating _censorship in China_. AFAIK a  free NYTimes copy in Chinese and kind of a proxy to hop the Great CyberWall. 

If you are interested in more detail, you can read [the guardian][guardian], or other sources.

<blockquote>
<p>Don't mess with countries, specially with big countries. Unless you can.</p>
<footer><cite>Albert Camps</cite></footer>
</blockquote>

The attack is cleverly played and instead of installing malware on the victims computer, it modifies a _javascript_ that would usually be used for Baidu's Analytics - Google's Chinese equivalent- for attacking [Github][gh].

To serve this modified content, it looks like _someone_ is interfering the connections that enter and leave **China**, and modifying Baidu's _javascript_.

I sincerely hope that this stops, and that the guys at [Github][gh] can sleep soon enough.

You can check the current status of the attack [here][twitter-status].

What do you think?

[gh]: http://www.github.com
[ddos]: http://en.wikipedia.org/wiki/Denial-of-service_attack
[twitter-status]: http://www.twitter.com/githubstatus
[attack-tweet]: https://twitter.com/githubstatus/status/582562501247811584
[guardian]: http://www.theguardian.com/technology/2015/mar/30/github-cleans-up-cyber-attack