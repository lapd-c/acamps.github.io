---
layout: post
title: "Programming hooks"
---

commit hooks

check files

diffable_files = `git diff --name-only --diff-filter=ACMRTUXB origin/master... | grep .md`.split("\n")

ddf="git diff --name-only --diff-filter=ACMRTUXB origin/master..."