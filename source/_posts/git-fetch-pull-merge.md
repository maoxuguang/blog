---
title: git fetch/pull/merge
date: 2017-02-28 22:08:57
tags:
---

git用起来比svn复杂很多，就在于很多操作涉及远程和本地，而svn把代码check out下来之后，在本地只做修改，提交，更新都针对远端。

命令格式：
```
git fetch remote_name branch_name
git pull remote_name branch_name
```
git fetch和git pull两个命令，要从远程主机取代码，需要指定远程主机和远程分支名，fetch取下所有分支，并不合并。pull合并到你当前所在本地分支。svn里面就不用这么麻烦，URL直接到branch的级别，但git里面URL只到repository的级别。要分别指定远程主机和分支。

svn的各个本地分支就是各个文件夹，也比git直观。

而git merge这个命令把指定分支合并到当前所在分支，我的理解这个操作是针对本地分支的,指定的分支和当前分支都是本地分支。有待验证。
>> 是的，git merge, git rebase 都是针对本地操作的，所以你需要先将远程的分支git fetch下来，然后才能进行git checkout, git merge和git rebase的操作。
