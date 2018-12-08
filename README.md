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

日志信息是过去所有提交过的版本的版本号（commit id），是一堆由SHA1计算出来的十六进制的数字。

## git reset

```bash
git reset --hard HEAD^ # 回到上一个版本，想回到上几个版本，就加几个^
git reset --hard HEAD~20 # 制定回到上20个版本，如果要回到很久以前的版本，这种方式比上一种更简单
git reset --hard <commit id> # 也可以使用commit id来指定回到哪一个版本
```

`HEAD`表示的是当前版本号，在git中用`HEAD`来指向当前的版本号。

## git reflog

```bash
git reflog # 这个命令用来记录每一次你执行的每一次git命令，也会显示所有commit过的版本号，如果回到以前的版本，又想回到最新的版本但是又不知道版本号，可以用这个命令来查看
```

## git checkout -- <file>

```bash
git checkout -- file # 撤销命令，丢弃工作区的修改，回到更改前的状态
```

有两种情况

1. 如果文件修改以后没有添加到暂存区，那么撤销之后会回到和之前一样的状态
2. 如果文件已经添加到暂存区，又修改了，那么撤销之后会回到添加到暂存区的状态

## git reset HEAD <file>

```bash
git reset HEAD <file> # 撤销暂存区的修改，把add到暂存区的内容撤销掉
```

总结

场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- file`。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD <file>`，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考[版本回退](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013744142037508cf42e51debf49668810645e02887691000)一节，不过前提是没有推送到远程库。

## git rm <file>

```bash
git rm <file> # 使用rm删除文件之后，如果真的是要删除，那就执行git rm <file>，然后commit一下就行了
# 如果是误删了，那就用git checkout -- <file>来丢弃工作区的修改。
```

## 远程命令

```bash
git remote add origin git@server-name:path/repo-name.git # 关联一个远程库和本地库
git push -u origin master # 第一次推送master分支的所有内容
git push origin master # 第一次推送用了-u之后，以后每次推送修改，都可以使用这个命令推送到远程库
```

第一次推送`master`分支的时候，加上了`-u`参数，Git不但会把本地的`master`分支内容推送的远程新的`master`分支，还会把本地的`master`分支和远程的`master`分支关联起来，在以后的推送或者拉取时就可以简化命令。