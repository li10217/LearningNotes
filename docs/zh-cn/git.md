
# Git 
# 在Windows上安装Git

* 从Git官网直接[下载安装程序](https://git-scm.com/downloads)，然后按默认选项安装。

* 安装完成后，还需要最后一步设置，在命令行输入：

```
$ git config --global user.name "Your Name" 
$ git config --global user.email "email@example.com"

```

# 创建版本库

## 本地仓库
```
<!-- 进入目录D: -->
$ cd /d/
<!-- 创建版本库gitproject-->
$ mkdir gitproject
<!-- 进入版本库gitproject-->
$ cd gitproject
<!-- 初始化版本库-->
$ git init
```
## 远程仓库

#### 关联远程仓库
?> 1.先查看Administrator目录下有没有`.ssh`目录,如果有，再看看这个目录下有没有`id_rsa`和`id_rsa.pub`这两个文件，如果已经有了，可直接跳到下一步,如果没有，打开Git Bash，创建SSH Key：
```cmd
$ ssh-keygen -t rsa -C "youremail@example.com"
```
?> 2.登陆GitHub，打开“Account settings”，“SSH Keys”页面,点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容

?> 3.git remote add origin git@server-name:path/repo-name.git 关联远程仓库

?> 4.关联后，使用命令git push -u origin master第一次推送master分支的所有内容。此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改

#### 从远程库克隆
?> $ git clone git@github.com:li10217/gitproject.git  还可以用https://github.com/li10217/gitproject.git 这样的地址。

* `git remote -v` 显示远程库的信息

# 常用操作

* `$ git status` 查看仓库当前状态
* `$ git diff readme.txt` 查看修改内容

## 修改提交
* `$ git add readme.txt` 添加单个修改到仓库
* `$ git add .` 添加所有修改到仓库
* `$ git commit -m "本次提交说明" ` 提交所有新添加的修改
* `git checkout -- file` 撤销修改，也可以用来恢复误删除的文件，回到最近一次add/commit时的状态，命令中的`--`很重要，没有`--`，就变成了“切换到另一个分支”的命令
* `$ git push origin master ` 提交到远程github仓库
* `$ git push origin dev` 提交dev分支

## 查看修改记录
* `$ git log` 查看仓库修改记录
* `$ git log --pretty=oneline` 查看简化记录

## 版本回退
* `$ git reset --hard HEAD^` 版本回退，上一个版本是`HEAD^`，上上一个版本就是`HEAD^^`,也可以写成`HEAD~100`。
* `$ git reset --hard commit_id` 指定回退版本号`v commit_id`

## 分支管理

* `$ git checkout -b dev` 创建`dev`分支，并切换到`dev`分支，`git checkou`t命令加上`-b`参数表示创建并切换
* `git branch` 查看当前所有分支
* `$ git checkout master` 切换到主分支 
* `$ git merge <name>` 合并到主分支
* `$ git merge --no-ff -m "merge with no-ff" dev` 普通模式合并
* `$ git branch -d <name>` 删除分支
* `$ git stash` 保存当前修改，可恢复

!> `git merge`命令用于合并指定分支到当前分支 ，合并分支时，加上`--no-ff`参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而`fast forward`合并就看不出来曾经做过合并。