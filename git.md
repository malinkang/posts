---
title: Git使用
date: 2016-11-25 11:22:54
tags: ["Git"]
image: https://images.unsplash.com/photo-1700167395210-09d25fdab0f6?q=80&w=3174&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
---

## git remote 

```shell
git remote add origin git@gitee.com:malinkang/learngit.git #添加远程仓库
git remote remove origin #删除远程仓库
git remote -v #查看远程仓库地址
```



## 分支

```sh
git checkout -b v2.0.0 #创建分支
git checkout v1.0.0 #切换分支
git merge v1.0.0 #合并分支
git branch -d v1.0.0 #删除分支
git push origin --delete v2.0.0 #删除远程分支
git branch #查看分支
git branch -a #查看所有分支
```



## 标签

```sh
git tag -a v1.0.0 -m "版本1.0.0" #创建tag
git tag #查看所有tag
git tag -l "v1.*" #查看v1.开头的标签
git push origin --tags #推送所有标签
git push origin tag v1.0.0 #推送单个tag
git tag -d v1.0.0 #删除tag
git push origin --delete v2.2.0 #删除远程tag
```

## 参考

* [Pro Git](https://git-scm.com/book/zh/v2)

* [移除忽略的文件](https://stackoverflow.com/questions/7927230/remove-directory-from-remote-repository-after-adding-them-to-gitignore)

