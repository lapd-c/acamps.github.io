---
layout: post
title: "What is Octopress? Why use it?"
date: 2015-03-28T21:06:15+01:00
categories: blog
---
The answer to what is [Octopress][octo], may be changing at the moment of writing this article. On [this article][article] they mention _it was_ a [jekyll][jekyll] custom _theme_ with a few extra scripts to make your blogging easier.

But now is evolving to a _sophisticated_ set of blogging tools related to [Jekyll][jekyll] in order to ease your blogging experience.

It may sound the same said with different words, but what before was a _Rakefile_ now is a command, and this means that it comes more... polished.

<blockquote><p>Better use commands than scripts you don't understand</p><footer><cite>Albert Camps</cite></footer></blockquote>

I have to say, that I find it **awesome**. With the [Octopress gem][octo-gem] you can **publish**, **unpublish**, and generate new posts based on the templates.

```bash
$ octopress publish _draft/post.markdown
```

You can have templates for generating posts, and avoid writing always the same - which I was currently doing. By _default_, templates are located at `_templates`.

So without any fear you can run in your working blog directory, and it won't overwrite  any file unless you use the `-f` flag.

```bash
$ octopress init .
$ octopress new draft <title>
```

They offer more plugins/tools in [the Octopress Github page][octopress], which are worth exploring.

The only drawback of using this plugins is that if you want to use it with a [Github pages][gh-pages] installation, you may need to compile the code in your local and using the [Octopress deploy plugin][octo-deploy] upload the resulting `_site` as static content, instead of letting [Github][gh-pages] compile and generate the code for you.

**Warning**: do not place in the same `Gemfile` the current version of Octopress and gh-pages gems, since they trigger an error if put together.


[octo]: http://octopress.org/
[article]:  http://octopress.org/2015/01/15/octopress-3.0-is-coming/
[jekyll]: http://jekyllrb.com/
[octo-gem]: https://github.com/octopress/octopress
[octopress]: https://github.com/octopress
[gh-pages]: http://www.github.io
[octo-deploy]: https://github.com/octopress/deploy
