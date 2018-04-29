Git is version control System
Git is free software 

Git(window) 学习内容 ：
1. 	下载地址 ： https://git-scm.com/downloads；

2. 	安装

3.	配置	$ git config --global user.name "Your Name"
			$ git config --global user.email "email@example.com"
			
4.	创建文件	$ mkdir learngit
				$ cd learngit
				$ pwd
				/Users/michael/learngit
		
5.	初始化一个Git仓库，使用git init命令。
	添加文件到Git仓库，分两步：
	第一步，使用命令git add <file>，注意，可反复多次使用，添加多个文件；
	第二步，使用命令git commit，完成。
	
6.	HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。

	穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。

	要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。
	
7.	理解git 工作区、暂存区测试