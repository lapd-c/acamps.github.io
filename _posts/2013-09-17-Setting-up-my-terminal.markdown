---
layout: post
title:  "Setting up my terminal"
date:   2013-09-17 16:15:15
categories: mac terminal oh-my-zsh
---

So, let's say I installed everything back again, and yes I had my terminal set up, but now I wanted to make some small changes, that didn't take _that_ long, but they did take __longer__ than expected, so here you have the details.

First, you should keep [this][Special-Characters] at hand at all time, and you should know that I use [Steve Losh Guide][Awesome-zsh] as a guide. It is all based on [Zsh terminal][oh-my-zsh] and [iTerm2][iterm2].

Also some of the information was retrieved from already existing themes, like smt, ys, sorin, and absolutely based on robbyrussell.

```
function battery_charge {
    echo `/Users/albertcamps/bin/batcharge.py` 2>/dev/null
}

PROMPT='%{$fg[magenta]%}%n%{$reset_color%} at %{$fg[yellow]%}%m%{$reset_color%} deep into %{$fg[cyan]%}%d%{$reset_color%}
%{$fg_bold[red]%}➜ %{$fg_bold[green]%}%p %{$fg[cyan]%}%c %{$fg_bold[blue]%}$(git_prompt_info)%{$fg_bold[blue]%} % %{$reset_color%}'

ZSH_THEME_GIT_PROMPT_PREFIX="git:(%{$fg[red]%}"
ZSH_THEME_GIT_PROMPT_SUFFIX="%{$reset_color%}"
ZSH_THEME_GIT_PROMPT_DIRTY="%{$fg[blue]%}) %{$fg[yellow]%}✗%{$reset_color%}"
ZSH_THEME_GIT_PROMPT_UNTRACKED="%{$fg[green]%}?"
ZSH_THEME_GIT_PROMPT_CLEAN="%{$fg[blue]%})"

RPROMPT='$(battery_charge)'
```

And the code for the batcharge.py is:

```python
#!/usr/bin/env python
# coding=UTF-8

import math, subprocess

p = subprocess.Popen(["ioreg", "-rc", "AppleSmartBattery"], stdout=subprocess.PIPE)
output = p.communicate()[0]

o_max = [l for l in output.splitlines() if 'MaxCapacity' in l][0]
o_cur = [l for l in output.splitlines() if 'CurrentCapacity' in l][0]

b_max = float(o_max.rpartition('=')[-1].strip())
b_cur = float(o_cur.rpartition('=')[-1].strip())

charge = b_cur / b_max
charge_threshold = int(math.ceil(10 * charge))

# Output

total_slots, slots = 10, []
filled = int(math.ceil(charge_threshold * (total_slots / 10.0))) * u'▸'
empty = (total_slots - len(filled)) * u'▹'

out = (filled + empty).encode('utf-8')
import sys

color_green = '%{[32m%}'
color_yellow = '%{[1;33m%}'
color_red = '%{[31m%}'
color_reset = '%{[00m%}'
color_out = (
    color_green if len(filled) > 6
    else color_yellow if len(filled) > 4
    else color_red
)

out = color_out + out + color_reset
sys.stdout.write(out)
```

[Special-Characters]:http://www.acm.uiuc.edu/workshops/zsh/prompt/escapes.html
[Awesome-zsh]:http://stevelosh.com/blog/2010/02/my-extravagant-zsh-prompt/
[oh-my-zsh]:https://github.com/sjl/oh-my-zsh/
[iterm2]:http://www.iterm2.com/
