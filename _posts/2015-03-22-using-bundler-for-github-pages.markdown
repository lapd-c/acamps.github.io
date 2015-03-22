---
title: "Using bundler for Github pages"
categories: jekyll bundler
date: 2015-03-22 22:30:34
layout: post
---
I come more from a **Javascript** / **PHP** background, so I had never worked with [bundler][bnd], and I was having issues finding it online until I found [this](https://help.github.com/articles/using-jekyll-with-pages/) explanation page.

It works almost exactly as [npm][npm] or [composer][composer] I only need to specify what I want to install and _boilà_!

In my scenario, with [Jekyll][jekyll] and [Github pages][gh-pages] I only need:

```
source 'https://rubygems.org'
gem 'github-pages'
gem 'jekyll-sitemap'
```

[Github pages][gh-pages] allow us to use the [jekyll-sitemap][j-sm] plugin, so to have feel in our local, we need to use it like this.

Finally, the biggest difference is, instead of `jekyll serve` I need to run:

```bash
$ bundle exec jekyll serve
```

Which is _extremely_ verbose for my taste. So I will **aliasize** it as soon as possible.

<blockquote>
<p>
Always create <em>alias</em> for your repetitive actions. You'll save the world.
</p>
<footer><cite>Albert Camps</cite></footer>
</blockquote>

[npm]: https://www.npmjs.com/
[composer]: https://getcomposer.org/
[bnd]: http://bundler.io/A
[jekyll]: http://www.jekyllrb.com
[gh-pages]: https://pages.github.com/
[j-sm]: https://github.com/jekyll/jekyll-sitemap
