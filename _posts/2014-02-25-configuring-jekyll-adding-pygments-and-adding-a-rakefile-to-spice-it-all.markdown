---
title: "Configuring Jekyll, adding pygments, and adding a Rakefile to spice it all. On Mac OS X Mavericks."
layout: post
tags : [how-to, jekyll]
categories: bloging
---
If you were updating from a previous Mac OS X version to Mavericks, most likely you have ruby on the system, but not a version you want to keep. So you'll first will need to:

{% highlight bash linenos %}
#Install rvm
$ \curl -sSL https://get.rvm.io | bash -s stable

#Install the new ruby version, 2.1.1 at the writing of this post, but list known will list them all
$ rvm list known
$ rvm install ruby-2.1.1
$ rvm use 2.1.1
{% endhighlight %}

Then you will have installed a new version of Ruby, and you can install [jekyll][jekyll] (easily with `gem install jekyll`, more in their site) and whatever markdown parser you want to install.

The rakefile you can find [here][gummesson_rakefile], will help you to get started, but needs to be spiced in order to show the posts in the form I intend them to be shown.

Also it is important to know that your `_config.yml` file has to be slightly modified to contain the following:

{% highlight yaml linenos  %}
#Blog settings
name: Your blog name
markdown: maruku
pygments: true
encoding: utf-8

#Settings for the rakefile
post:
  template: _post.txt
  extension: markdown
page:
  template: _page.txt
  extension: markdown
editor: vim
git:
  branch: master
transfer:
  command: rsync
  settings: -av
  source: _site/
  destination: ~/Any/Folder/You/choose/your-gh-page.github.io/
{% endhighlight %}

Setting the encoding will make your life a lot easier.

Finally, you need to have pygments installed. That can be _easilly_ accomplished with
{% highlight bash linenos %}
$ sudo easy_install pip
$ sudo pip install pygments
{% endhighlight %}

Otherwise problems with the encoding might arise.

To see how your server is behaving, and check if everything is working fine:
`jekyll serve --drafts -w`
and immediately you will see your posts, your drafts, and everything on http://localhost:4000 . Also, it  will get updated once it's modified, because of the -w (watch) flag.

[jekyll]: http://jekyllrb.com/
[gumesson_rakefile]: https://github.com/gummesson/jekyll-rake-boilerplate/blob/master/Rakefile
