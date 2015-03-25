---
title: "git - Remove files from history. How to store sensitive data."
layout: post
categories: git security
---
Today I had a _funny_ issue at work. Note that where I say _funny_ I mean serious, and distressful.

I committed sensitive information to a public **git** repository. I won't disclose more, for security reasons, but I will share how I _cleaned_ the mess up.

An alarm was triggered for an exposed token and Andrés from the Systems department at [Social Point][sp] notified me, just 2 hours after my fatal push.

Luckily at [Stack overflow][stack] it is easy to find solution to this kind of questions.

```bash
git filter-branch --index-filter \
'git update-index --remove filename' <introduction-revision-sha1>..HEAD
git push --force --verbose --dry-run
git push --force
```

As they mention it is answered by [Github][gh] as a FAQ, in a detailed article that I recommend reading.

After that, I asked to Andrés what I could do to avoid this again, and he gave me the following instructions:

I had to add to my `.zshrc` a few new lines indicating where the _sensitive_ information would be placed now. Following Andrés' advice, I decided to **create a new folder called `private`** in case I needed to put more sensitive information there in the future:

```bash
source private/private_keys.txt
```

And this `private_keys.txt` file contains what should be hidden:

```bash
export APP_PRIVATE_KEY=<key>
export APP_SECRET_SECRET=<secret>
export RESOURCE_SECURITY_TOKEN=<token>
```

Finally, I have had to add the `private` folder to `.gitignore` to avoid more painful mistakes:

```bash
*.swp
private/
```

I'll check [this article][script] on how to have a script that automates this task for me. And even create my own to remove just one string from all history, based on [this Stack overflow question][soq].

Today I won't joke with my cite.

<blockquote>
<p>Be very aware of what you are committing to your <em>dotfiles</em> repository. You may end up doing more harm than good.</p>
<footer>
<cite>Albert Camps</cite>
</footer>
</blockquote>

Have you ever had similar issues? How do you solve this?

[dotfiles]: http://www.github.com/acamps/dotfiles
[stack]: http://stackoverflow.com/questions/872565/remove-sensitive-files-and-their-commits-from-git-history
[gh]: https://help.github.com/articles/remove-sensitive-data/
[amazon]: http://aws.amazon.com/?nc1=f_ls
[script]: http://dound.com/2009/04/git-forever-remove-files-or-folders-from-history/
[soq]: http://stackoverflow.com/questions/7194939/git-change-one-line-in-file-for-the-complete-history
[sp]: http://www.socialpoint.es
