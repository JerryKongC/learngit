Git is version control System
Git is free software 

Git(window) 学习内容 ：
1下载. 	下载地址 ： https://git-scm.com/downloads；

2安装. 	安装

3配置.	配置	$ git config --global user.name "Your Name"
			$ git config --global user.email "email@example.com"
			
4创建版本库.	创建文件	$ mkdir learngit
				$ cd learngit
				$ pwd
				/Users/michael/learngit
		
5创建版本库.	初始化一个Git仓库，使用git init命令。
				添加文件到Git仓库，分两步：
				第一步，使用命令git add <file>，注意，可反复多次使用，添加多个文件；
				第二步，使用命令git commit，完成。
	
6版本回退.	HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。

			穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。

			要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。
	
7工作区和暂存区.	工作区 ——add——> 版本库(stage ——commit——>master)

8管理修改. 	git管理的是修改而不是文件

9.撤销修改. 场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
			场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。
			场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。
			
10.删除文件.	命令git rm用于删除一个文件。如果一个文件已经被提交到版本库，那么你永远不用担心误删，但是要小心，你只能恢复文件到最新版本，你会丢失最近一次提交后你修改的内容。

11添加远程库.	要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git；
				关联后，使用命令git push -u origin master第一次推送master分支的所有内容；
				此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；
				分布式版本系统的最大好处之一是在本地工作完全不需要考虑远程库的存在，也就是有没有联网都可以正常工作，而SVN在没有联网的时候是拒绝干活的！当有网络的时候，再把本地提交推送一下就完成了同步，真是太方便了！		

12克隆远程库.	要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。
				Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快。				
				
13创建与合并分支.	查看分支：git branch
					创建分支：git branch <name>
					切换分支：git checkout <name>
					创建+切换分支：git checkout -b <name>
					合并某分支到当前分支：git merge <name>
					删除分支：git branch -d <name>
					
14解决冲突.		当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。
				用git log --graph命令可以看到分支合并图。
				
15分支管理策略.		合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。		

16错误分支. 	当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场。

17.feature分支.	 	开发一个新feature，最好新建一个分支；

					如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除。
					
18多人协作.		master分支是主分支，因此要时刻与远程同步;
				dev分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步;
				错误分支只用于在本地修复错误，就没必要推到远程了，除非老板要看看你每周到底修复了几个错误;
				设有分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。
				
19创建标签		命令git tag <name>用于新建一个标签，默认为HEAD，也可以指定一个commit id;
				git tag -a <tagname> -m "blablabla..."可以指定标签信息;
				git tag -s <tagname> -m "blablabla..."可以用PGP签名标签;
				
20操作标签		命令git push origin <tagname>可以推送一个本地标签；
				命令git push origin --tags可以推送全部未推送过的本地标签；
				命令git tag -d <tagname>可以删除一个本地标签；
				命令git push origin :refs/tags/<tagname>可以删除一个远程标签。
