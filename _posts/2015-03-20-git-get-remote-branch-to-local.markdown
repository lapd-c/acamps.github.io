---
layout: post
title: "Git - get remote branch to local"
date: 2015-03-20 20:38:00
categories: git
---
More often than not, I find myself googling how to **get a remote branch** from one of my colleagues [feature branch][git-flow] to my local. 

```bash
$ git checkout -b feature/branchName origin/feature/branchName
```

Easy enough. But my colleagues, they use [SourceTree][st]. Blame on them.

<blockquote>
	<p>
	Use git on the command-line. Be a man.
	</p>
	<footer>
		<cite>
			Albert Camps
		</cite>
	</footer>
</blockquote>

----

At [Social Point][sp] analytic's department we currently develop our code using [git-flow][gf], a well-thought methodology for managing the **inclusion of features** into a succession of gradual product releases.

I had previously worked with [git][git] and [git-flow][gf], but not using it in a team.

We currently separate our work into feature branches, that one reviewer has to check and merge before they are done. I find the [code reviews][cr] insightful, pleasurable and challenging. If you do not work in this manner, I really would recommend you do.


[git-flow]: http://danielkummer.github.io/git-flow-cheatsheet/
[sp]: http://engineering.socialpoint.es
[gf]: http://nvie.com/posts/a-successful-git-branching-model/
[st]: https://es.atlassian.com/software/sourcetree/overview
[git]: http://www.git-scm.com
