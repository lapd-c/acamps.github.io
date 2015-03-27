---
title: "Multiple ssh identities. My auto-committer with private repositories"
layout: post
categories: git productivity ssh
---
My [auto-committer][post] does not work with private repositories. Yes you can automate commits, but **no pulls or pushes allowed**.

In order to solve this issue, the simpler way I know is to [generate a ssh key][key] and include it into your [Github][gh] keys. Before you follow the link and the instructions provided there, I _must warn you_ that if you want a cron to run the command in your behalf, you need to specify an **empty passphrase** in the key.

I will take for granted that you have **more than one** ssh user, and explain what to do given that is the case. If not, probably it works out-of-the-box, but the end of the article maybe helpful _otherwise_.

The `~/.ssh/config` file contains all the specific hosts where you can have multiple identities. At this moment you may need to add the second; _[acamps][acamps]_ in my case.

```bash
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
```

As you can see, I have both my work account, and my personal account set up.

Then, for example, in my _[acamps.github.io][blog]_ repository I have the `.git/config` file like follows:

```bash
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = false
[remote "origin"]
    url = ssh://git@github.com-acamps/acamps/acamps.github.io.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[branch "feature/pixyll-migration"]
    remote = origin
    merge = refs/heads/feature/pixyll-migration
```

Where the important part is that I am referencing **github.com-acamps** as the host in the **url**.

Simply with that, _every next push in this repository will be done with the matching ssh identity_, and you can work with two accounts at the same time, configuring it in the `.git/config` file and forgetting about it forevermore.

<blockquote>
<p>
Do your best to have easy to maintain setups, so you can be lazy afterwards.
</p>
<footer><cite>Albert Camps</cite></footer>
</blockquote>

Keep in mind that this works because you have executed:

```bash
$ ssh-add /Users/albertcamps/.ssh/id_rsa_2
```

So in _my auto-committer_, that will be executed from within a cron, we must **add the identity too*, and a way of doing so, thanks to [a stack overflow post][so] is:

```bash
ssh-agent bash -c 'ssh-add /Users/albertcamps/.ssh/id_rsa_2; git clone git@github.com:acamps/acamps.github.io.git'
```

The resulting auto-committer updated can be seen in the following gist:

{% gist 5912e597bef229de40b5 %}

[key]: https://help.github.com/articles/generating-ssh-keys/
[blog]: http://www.albertcamps.io
[gh]: http://www.github.com
[so]: http://stackoverflow.com/questions/4565700/specify-private-ssh-key-to-use-when-executing-shell-command-with-or-without-ruby
[post]: http://www.albertcamps.io/productivity/2015/03/25/my-auto-committer/
[acamps]: http://www.github.com/acamps