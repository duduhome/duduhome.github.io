---
title: "Git"
layout: page
date: 2099-06-02 00:00
---
[TOC]
#Git基本使用#
##创建版本库 ##

	mkdir learngit
	cd learngit
	git init //初始化为git可以管理的仓库

##提交和修改##
###基本命令###
查看当前状态

    git status

查看readme文件被修改的内容

    git diff readme.txt

查看历史提交记录，其中一大串数字为commit id（版本号）

    git log

###提交###
把文件提交到暂存区

    	git add readme.txt //提交某个文件
	git add . //提交全部文件

把文件从暂存区提交到当前分支

    	git commit -m ‘comment’

###回退版本###

回退到上一个版本，如果是上上个版本HEAD^^,依次类推HEAD^^^...100可以写为HEAD~100

		git reset --hard HEAD^

回退到某一个版本，这串数字就是之前提到的版本号，版本号写个几位就可以了，git会自动寻找到

		GIT RESET --hard 233543234

###修改和删除###

丢弃工作区的修改，回到最近依次的git add或者git commit

	git checkout —- file

直接把文件删除了，或者使用了rm命令删除了文件，把文件从仓库中清除

	git rm filename

##远程仓库##
###添加远程仓库###
最简单的就是在github上创建一个自己的远程仓库，然后把本地仓库与远程仓库进行关联

	git remote add origin git@github…

###克隆远程仓库###
另外一种关联远程仓库的方法，把远程仓库克隆下来，包括所有分支

	git clone git@github…

###提交远程代码###
将本地提交好的分支，推送到远程分支上

	git push origin branch_name

##分支管理##
###创建本地分支###
创建一个本地分支，-b代表创建分支并且切换到此分支

	git checkout -b branch_name

相当于

	git branch name
	git checkout name

创建本地分支与远程分支关联，假如本地无mywiki分支，远程存在mywiki分支

	git checkout -b branch_name origin/branch_name

###查看当前分支###

	git branch

其中*表示当前分支

###切换分支###

	git checkout name

###合并分支###
合并某分支到当前分支

	git merge name

###删除分支###

	git branch -d name
