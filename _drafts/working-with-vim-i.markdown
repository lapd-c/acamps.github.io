---
title: "Working-with-VIM-I"
layout: post
tags: "vim"
---
Most unix-based systems come with VIM, a handy editing tool that allows a huge amount of flexibilty and that can be customized to a great extent.

I have heard that emacs is awesome too, but more people close to me can teach me VIM than emacs, so this kinds of sorts it.

In my configuration file, `~/.vimrc` I usually turn line numbers on, configure tab to be spaces (4) end, and a few more things. Right now Paco has helped me with a few things. Actually this allows me to work with more than one file.

My updated dotfiles can be found [dotfile][here].

PD: an interesting way of forcing yourself to get used to vi, is to edit terminal behaviour to emulate vi.

This can be done by adding the following to your `.zshrc` file. Or `.bashrc` file in the terrible case you use bash.
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

It gets a bit crazy learning vim, since everything is different, and there's a myriad of ways to do the same thing.

In normal mode, the features I find more useful so far are:

i   insert
$   end of line
w   advance word
W   advance WORD
b   back word
B   back WORD
dd  delete line
0   start of line
/pattern    search   fun to use with :set hlsearch
n   next
A   append at the end of line
a   append
u   undo
.   repeat last action (which might be much more than you thing)
G   go to the end of the document
gg  go to the beggining of the document
cit     change inner t   so it changes the content inside t
:#lineNumber    Jumps to a line number

This last option shows to be quite awesome, since you can quickly move to a word inside quotes with /pattern, or f{char} and then cit to delete the whole content. It also works with single quote, t (tag, usefull for html), and probably something else yet to discover.

Of course, the magic in vim resides in the fact that you can repeat actions super easily, that you can combine keys, and so on. I'm not going to go into deep detail, but:

dw  deletes a word
db  deletes a word back
d0  deletes from cursor to begining of file
d$  deletes from cursor to the end of file

It is true that this can be done with other shortcuts in different editors like cmd+delete in mac. 
Options I recommend and find quite usefull
:set number       this allows to use very easilly :#numberline to jump straight there
:set cul          adds an horizontal line below the position of the cursor, so it can be easilly spotted.

And finally some options to add to your `.vimrc`, in order to work easilly with folders while in the vim file navigator.
{% highlight bash %}
let g:netrw_liststyle=3 
let g:netrw_browse_split=4 
let g:netrw_preview=1 
let g:netrw_winsize=35
{% endhighlight %}

Whether it is true that the learning curve is not too fast, it gets interesting coding this way. Then you begin getting a grasp of it with features like :tabedit, plugins, markers, and a lot of other stuff that I am just starting to find.

Awesome.

Painfull.

[dotfile]: http://www.github.com/acamps/dotfiles
