---
title: "My auto-committer with private repositories"
layout: post
categories: git productivity ssh
---
My auto-commiter does not work with private repositories. Yes you can automate commits, but **no pulls or pushes allowed**.

In order to solve this, one way is to [generate your own ssh key][key] and include it into your [Github][gh] keys. Before you follow the link and the instructions provided there, I _must warn you_ that if you want a cron to run in your behalf, you need to specify an **empty passphrase**.

I will take for granted that you have more than one user, and since that is the case.Once that is done you need to change the config http://stackoverflow.com/questions/4565700/specify-private-ssh-key-to-use-when-executing-shell-command-with-or-without-ruby

config
#github for sp-albert-camps
Host github.com-sp
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa

#github for acamps
Host github.com-acamps
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_2

Host github.com-me
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_me

https://help.github.com/articles/generating-ssh-keys/
