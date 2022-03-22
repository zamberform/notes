---
layout: blog
title:  "GitでのUnityソース管理"
date:   2018-01-15
category: Unity
istop: true
background-image: http://4.bp.blogspot.com/-Mtc2YFmvsXY/VlWTU5YEr3I/AAAAAAAAAE0/iQDERs9dUH4/s1600/git-logo.jpg

---

# GLF

Git Large File Storageの略称はGLFになります。Gitで扱うファイルの最大サイズが5M超えた場合の対策になります。

基本的にゲーム開発しながら、5M超えるファイルは必ず存在しています、これらもGitでうまくコントロールしたい場合、GLFを入れなくちゃいけない。

# GitFlow

[Git Flow](http://nvie.com/posts/a-successful-git-branching-model/)の概念を使って、ソースを管理するのはすごく優れた考えです。

masterはリリースのために存在しているのため、全ての作業はdevelopのブランチに集中する。

[Git Flow](http://nvie.com/posts/a-successful-git-branching-model/)は、developのブランチをmasterにマージするに、この目的だけの存在。

まだ、developの下にもう一個のブランチで、すべてのブランチ（各機能）のソースを統一化してもらう。

という流れのようです。

# GitIgnore

[Unity専用 .gitignore](https://github.com/github/gitignore/blob/master/Unity.gitignore)


