---
title: "Git"
layout: page
date: 2099-06-02 00:00
---
[TOC]
#本地和远程关联#

##初始化 ##

	git init

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
