---
layout: post
title: "Issues using Defaults in Jekyll"
date: 2015-03-29T21:51:56+02:00
categories: blog jekyll
---

Keeping in mind the [DRY][dry] principle, I want to write as less as possible when working on a blog post.

Given than [Jekyll][jekyll] provides a few ways of helping in this, let's see how to stop typing at the beginning of each post:

```bash
layout: post
```

According to [Jekyll's configuration][config], adding the following, would be enough:

```bash
defaults:
  -
    scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
```

But an error pops out saying that :

```bash
Build Warning: Layout 'post' requested in <file> does not exist.
```

I have been trying to get past it, but _without success so far_.

**Starting out with a new blog, and adding this lines, it works**, so it _may_ have to do with the template I am using. Tomorrow I'll figure this out.

<blockquote>
<p>Always report bugs you find, you may help someone not get fired.</p>
<footer><cite>Albert Camps</cite></footer>
</blockquote>

[dry]: http://en.wikipedia.org/wiki/Don%27t_repeat_yourself
[jekyll]: http://www.jekyllrb.com
[config]: http://jekyllrb.com/docs/configuration/
