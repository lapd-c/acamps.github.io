---
title: "Configuring Jekyll, adding pygments, and adding a Rakefile to spice it all. On Mac OS X Mavericks."
layout: post
tags : [how-to, jekyll]
categories: bloging
---
The rakefile you can find [here][gummesson_rakefile], needs to be spiced in order to show the posts in the form I intend them to be shown.

Also it is important to know that your `_config.yml` file has to be slightly modified to contain the following:

{% highlight yaml linenos  %}
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
$ sudo pip pygments
{% endhighlight %}

