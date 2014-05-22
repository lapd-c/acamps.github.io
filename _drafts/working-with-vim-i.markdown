---
title: "Working-with-VIM-I"
layout: post
tags: "vim"
---
Most unix-based systems come with VIM, a handy editing tool that allows a huge amount of flexibilty and that can be customized to a great extent.

I have heard that emacs is awesome too, but more people close to me can teach me VIM than emacs, so this kinds of sorts it.

In my configuration file, `~/.vimrc` I usually turn line numbers on, configure tab to be spaces (4) end, and a few more things. Right now Paco has helped me with a few things. Actually this allows me to work with more than one file.

My updated dotfile can be found [dotfile][here].

PD: an interesting way of forcing yourself to get used to vi, is to edit terminal behaviour to emulate vi.

This can be done by adding the following to your `.zshrc` file.
{% highlight bash %}
set -o vi
{% endhighlight %}

Additionally, you can disable mapping of arrow keys in vim edition mode, just in order to replace an old habit with a new one, so you just become more profficient out of the box. This can be done editing your `.vimrc` file, adding this:

{% highlight bash %}
noremap <Up> <NOP>
noremap <Down> <NOP>
noremap <Left> <NOP>
noremap <Right> <NOP>
{% endhighlight %}

This, however, will allow you to still use arrows on insert mode, but not in normal mode.



{% highlight bash %}
let g:netrw_liststyle=3 " Use tree-mode as default view
let g:netrw_browse_split=4 " Open file in previous buffer
let g:netrw_preview=1 "_ preview window shown in a vertically split
let g:netrw_winsize=35
{% endhighlight %}
