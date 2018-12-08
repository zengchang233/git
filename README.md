# Git

> Git 基础命令说明书

[TOC]

## git概念

用git对一个项目进行版本控制，可以分为三个区域，工作区（working directory），暂存区（staging index）和仓库区（repository）。工作区就是项目所在的那个目录，所有非隐藏文件都在工作区，暂存区可以从`.git`这个文件夹里面找到一个叫`index`的文件，这就是暂存区，仓库区是`.git`这个文件夹除了`index`这个文件的其余区域。

## git init

```bash
git init # 初始化一个git仓库
```

## git add <file>

```bash
git add file1 file2 ... # 添加文件到暂存区里面
```

## git commit -m <message>

```bash
git commit -m "message string" # 提交暂存区里面的文件到仓库区中
```

## git status

```bash
git status # 显示当前仓库的状态
```

## git diff

```bash
git diff # 查看当前修改但是没有add的文件，与上次已经commit文件之间的区别
```

## git log

```bash
git log # 显示日志信息
git log --pretty=oneline # 在一行里面显示精简的日志信息
```



