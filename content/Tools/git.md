---
title: "Git"
layout: page
date: 2099-06-02 00:00
---
[TOC]
#本地和远程关联#

##创建版本库 ##

	mkdir learngit
	cd learngit
	git init //初始化为git可以管理的仓库

##提交和修改##
###基本命令
查看当前状态

    git status

查看readme文件被修改的内容

    git diff readme.txt

可以查看历史提交记录，其中一大串数字为commit id（版本号）

    git log

###提交###
把文件提交到暂存区

    	git add readme.txt

把文件从暂存区提交到当前分支

    	git commit -m ‘comment’

###回退版本###

		git reset --hard HEAD^ //回退到上一个版本，如果是上上个版本HEAD^^,100可以写为 HEAD~100
		GIT RESET --hard 233543234 //回退到某一个版本，这串数字就是之前提到的版本号，版本号写个几位就可以了，git会自动寻找到

##创建本地分支##

	git checkout -b branch_name//branch_name与远程分支name一致

##建立远程仓库##

	git remote add origin git@地址

##远程分支关联##

	//若远程无分支，以下命令会自动创建分支
	git push -u origin branch_name
	
	//若远程存在分支
	git pull git@地址 <远程分支>:<本地分支>
	
##本地提交##

	git add .
	git commit -m 'comment'
	git push -u origin branch_name
