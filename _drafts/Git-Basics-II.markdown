---
title:Git Basics II
layout: post
---
How to create a git remote

# In the folder you want to place the git remote
cd /folder/you/choose
mkdir folderForGitRemote
cd folderForGitRemote
git init --bare

Then you have a local folder that you want to copy to the remote, but first you have to initialise it as a git repository.
# Without the --bare option this time
cd /folder/that/contains/your/information
git init

git fetch
git remote -v
git remote add name url

git pull origin
To change the default
Edit your .git/config

or
git pull -u remote-name (git config https://www.kernel.org/pub/software/scm/git/docs/git-push.html)

comments on git rm
git rm -rf
git rm --cache
git add

Also it is usefull to tag some special commits, so you can go back to them when you need.

To see which tags have been created
git tag
to add a new tag
$ git tag -a v1.4 -m 'my version 1.4'

Setting your branch to exactly match the remote branch can be done in two steps:

git fetch origin
git reset --hard origin/master
If you want to save your current branch's state before doing this (just in case), you can do:

git commit -a -m "Saving my work, just in case"
git branch my-saved-work

[Example][http://www.keradgames.com/]
