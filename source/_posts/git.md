---
title: git
date: 2024-01-24 19:05:49
tags:
- method
---
# 我要成为git高手（雾）
### **初始化:绑定邮箱和账号**
```
git config --global user.name "ishland"
git config --global user.email 
```
### **创建本地仓库**
```
git init
git add .
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:Tree-Summer/Mei_Sai.git
```
### **创建本地，远程分支，推送**
```
git branch//查看本地分支
git branch -r//查看远程分支
git branch -a//查看所有分支
git branch [branch name]//创建本地新分支
git checkout [branch name]//切换到新分支
switched to branch ‘develop2’//也是切换
git checkout -b [branch name]//创建分支同时也切换分支
```
### **拉取**<br>
git pull:获取最新代码到本地，自动合并到当前分支
```
git remote -v//查询当前远程分支
git pull origin master//拉取远端origin/master分支合并到本地当前分支
git pull origin dev//拉取origin/dev分支
```
git fetch+merge:获取最新代码手动合并
```
git remote -v
git fetch orign master:master1//在本地建立master1分支，下载远端origin/master分支到master1分支
git diff master1 //查看本地master1分支与当前分支版本差异
git merge master1//合并本地分支master1到当前分支
git branch -D master1//删除本地分支master1
```
不额外建立本地分支
```
git remote -v
git fetch origin master
git log -p master..origin/master//查看本地master与远端origin/master的版本差异
git merge origin/master//合并远端分支origin/master到当前分支
```
### **上传**
```
git add .
git commit -m
git push origin [branch name]:[branch name]//推送本地新分支到远程仓库
git push origin develop2
```

### **手动合并**

### 连接问题
 ```
 ssh -T git@github.com //是否连接上
```

###  references
(https://blog.csdn.net/Thinkingcao/article/details/106059446)

### 删除
~~~
git ls-files //查看缓存区文件
git reset . //已经add .后，用该命令重置
git push origin --force //强制推送更改内容
~~~