---
title: "Git-III"
layout: post
---
# The importance of good commits and git diff.

It is important to, even usually it is easier to just `git add -A`, and commit a full coding (or several) sessions, not do so.

It is important to make *relevant* commits. Select files in semantic groups, and commit them together. In this way you can then follow what's been going on on a branch with much ease. And all that is going on will be reported, not a generic message like:

git commit -m "Add changes. heh. Works better -- I guess."


$ git diff --cached > changes.patch

$ patch -p1 < changes.patch --dry-run # to hide

$ git diff
