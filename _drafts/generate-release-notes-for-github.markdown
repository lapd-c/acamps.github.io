---
layout: post
title: "Generate Release Notes for Github"
---

ri = !f() { git loc `git lt`..develop --no-merges; }; f
loc = log --pretty=format:-\ (%h)\ %s
lt = describe --tags --abbrev=0

git lt te dice el último tag creado
git ri te muestra las diferencias entre el último tag y develop
y con git loc...
las diferencias entre lo que le digas
git loc develop..master
por ejemplo
git loc 1.0.0..1.1.0 --no-merges

https://developer.github.com/v3/repos/releases/#create-a-release

https://github.com/arzynik/github-auto-release
http://www.barrykooij.com/create-github-releases-via-command-line/
http://www.janosgyerik.com/deploying-new-releases-using-git-and-the-post-receive-hook/

http://stackoverflow.com/questions/9132144/how-can-i-automatically-deploy-my-app-after-a-git-push-github-and-node-js
