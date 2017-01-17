# Git 分支篇

- `Git Branching` Git 分支模型介绍
- `Feature Branch` 功能分支工作流
- 一个例子 

## Git Branching
Git 的分支模型是一个“Killing Feature”，它以一种难以置信的轻量方式处理分支，因此，鼓励在工作流程中频繁地使用分支与合并。
理解和精通这一特性，你便会意识到 Git 是如此的强大而又独特，并且从此真正改变你的开发方式。

- ☞ 为啥建分支这么快？ **分支本质上就是一个41字节的文件**
- ☞ 为啥合并这么快？ **三方合并机制**
- ☞ **本地的分支合并操作与远端的分支管理**

## Feature Branch
`功能分支工作流`仍然基于中央仓库，并且master分支还是代表了正式项目的历史。 但不是直接提交本地历史到各自的本地master分支，开发者每次在开始新功能前先创建一个新分支。 功能分支应该有个有描述性的名字，比如animated-menu-items或issue-#1061，这样可以让分支有个清楚且高聚焦的用途。

在master分支和功能分支之间，Git是没有技术上的区别，所以开发者可以用和集中式工作流中完全一样的方式编辑、暂存和提交修改到功能分支上。

另外，功能分支也可以 push 到中央仓库中。这样不修改正式代码就可以和其它开发者分享提交的功能。
由于master是仅有的一个『特殊』分支，在中央仓库上存多个功能分支不会有任何问题。
当然，这样做也可以很方便地备份各自的本地提交。

## Command List

### git branch - 查看、创建及删除分支

	☞ 'git branch -a'list both remote-tracking branches and local branches.

### git checkout - 切换分支



### git fetch - 抓取远程仓库内容，放入本地库

	☞ 'git fetch' fetches down all the information that is in that repository 
	that is not in your current one and stores it in your local database

### git pull - 抓取远程仓库内容，合并入当前分支

	☞ 'git pull' update for the repository cloned from, 
		   then merge one of them into current branch

### git rebase - [分支整合](https://git-scm.com/book/zh/v2/Git-分支-变基)

	☞ 'git rebase' reapply commits on top of another base tip

## 举个例子

在learn-git的编写中，采用功能分支工作流，我的预期是(Step 1 ~ 6)：

	- 以master为主干，与线上发布版本同步
	- 创建一个分支来开发新需求 (Step 1, checkout -b dev-li3huo)
	- 然后在这个分支上开展工作，完成后再合并到主干(Step 2 ~ 6, commit & pull)

在初版内容发布后，我在同步进行着修订。此时有朋友反馈意见，线上内容需要紧急修补。
为了应对这种：

	- 保存当前工作状态，然后切换回主分支（Step 7, checkout master）
	- 为紧急修复任务新建一个分支(Step 8, checkout -b hotfix)，并在其中修复它
	- 在测试通过之后，切换回线上分支，然后合并这个修补分支，最后将改动推送到线上分支(Step 9, checkout -b hotfix)
	- 切换回你最初工作的分支上，继续工作(Step 1, checkout dev-li3huo)


### Step 1：创建一个分支来开发新需求
首先，每次开发新功能，都应该新建一个单独的分支

	# 获取主干最新代码
	➜  learn-git git:(master) git checkout master     
	Already on 'master'
	Your branch is up-to-date with 'origin/master'.
	➜  learn-git git:(master) git pull
	Already up-to-date.

	# 新建一个开发分支myfeature
	➜  learn-git git:(master) git checkout -b dev-li3huo
	Switched to a new branch 'dev-li3huo'
	➜  learn-git git:(dev-li3huo) 

	☞ 'git checkout' is used to switch branches
	☞ 'git pull' update for the repository cloned from, 
		   then merge one of them into current branch
	☞ 'git checkout -b' is used to create and then switch branches

### 第二步：提交分支commit
分支修改后，就可以提交commit了

	➜  learn-git git:(dev-li3huo) ✗ git add .
	➜  learn-git git:(dev-li3huo) ✗ git status
	On branch dev-li3huo
	Changes to be committed:
	  (use "git reset HEAD <file>..." to unstage)

		new file:   git-process.md

	# 提交(在编辑器中填写提交信息)
	➜  learn-git git:(dev-li3huo) ✗ git commit --verbose
	[dev-li3huo 470a772] Git 标准使用流程
	 1 file changed, 94 insertions(+)
	 create mode 100644 git-process.md

### :point_right: 提交信息的格式

提交commit时，必须给出完整扼要的提交信息，下面是一个范本([提交信息书写规则](git-commit.md))


	Present-tense summary under 50 characters

	* More information about commit (under 72 characters).
	* More information about commit (under 72 characters).

	http://project.management-system.com/ticket/123

第一行是不超过50个字的提要，然后空一行，罗列出改动原因、主要变动、以及需要注意的问题。最后，提供对应的网址（比如Bug ticket）

### 第三步：主干与远端同步
分支的开发过程中，要经常与主干保持同步

	➜  learn-git git:(dev-li3huo) ✗ git fetch
	remote: Counting objects: 4, done.
	remote: Compressing objects: 100% (1/1), done.
	remote: Total 4 (delta 3), reused 4 (delta 3), pack-reused 0
	Unpacking objects: 100% (4/4), done.
	From https://github.com/twotwo/learn-git
	   27177fd..934621e  master     -> origin/master 

### 第四步：rebase dev-li3huo
分支开发完成后，很可能有一堆commit，但是合并到主干的时候，往往希望只有一个（或最多两三个）commit，这样不仅清晰，也容易管理。

那么，怎样才能将多个commit合并呢？这就要用到 git rebase 命令。

	➜  learn-git git:(dev-li3huo) git rebase master
	Current branch dev-li3huo is up to date.

git rebase命令的i参数表示互动（interactive），这时git会打开一个互动界面，进行下一步操作

### 第五步：把 rebase的内容一次性的合并到主干

	➜  learn-git git:(dev-li3huo) git checkout master
	➜  learn-git git:(master) git merge dev-li3huo
	Updating 27177fd..63ccd06
	Fast-forward
	 git-process.md | 151 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	 1 file changed, 151 insertions(+)
	 create mode 100644 git-process.md

### 第六步：合并后的主干推送到远程仓库
合并commit后，就可以推送当前分支到远程仓库了

	➜  learn-git git:(master) git push -u origin master
	To https://github.com/twotwo/learn-git.git
	 ! [rejected]        master -> master (non-fast-forward)
	error: failed to push some refs to 'https://github.com/twotwo/learn-git.git'
	hint: Updates were rejected because the tip of your current branch is behind
	hint: its remote counterpart. Integrate the remote changes (e.g.
	hint: 'git pull ...') before pushing again.
	hint: See the 'Note about fast-forwards' in 'git push --help' for details.

git push命令要加上force参数，因为rebase以后，分支历史改变了，跟远程分支不一定兼容，有可能要强行推送

	➜  learn-git git:(master) git push -u origin master --force
	Counting objects: 12, done.
	Delta compression using up to 8 threads.
	Compressing objects: 100% (12/12), done.
	Writing objects: 100% (12/12), 4.55 KiB | 0 bytes/s, done.
	Total 12 (delta 7), reused 0 (delta 0)
	remote: Resolving deltas: 100% (7/7), completed with 1 local objects.
	To https://github.com/twotwo/learn-git.git
	 + 934621e...63ccd06 master -> master (forced update)
	Branch master set up to track remote branch master from origin.

## 参考
- 《Pro Git V2》 3. Git 分支
	
	* [3.1 分支简介](https://git-scm.com/book/zh/v2/Git-分支-分支简介) 分支的基本原理，建议掌握一下，否则估计会搞不懂下面的例子
	* [3.2 新建与合并](https://git-scm.com/book/zh/v2/Git-分支-分支的新建与合并) 一个应用的例子
	* [3.4 常见工作流介绍](https://git-scm.com/book/zh/v2/Git-分支-分支开发工作流) 

		- `长期分支` 适用于对稳定性要求很高、复杂庞大的项目
		- `特性分支` 短期分支，对任何规模的项目都适用 - Git 特有的工作流

	* [3.5 远程分支](https://git-scm.com/book/zh/v2/Git-分支-远程分支) 远程分支的管理

		- `跟踪分支` git checkout --track origin/remote_branch
		- `拉取` pull == fetch + merge到跟踪分支
		- `删除远程分支` git push origin --delete remote_branch

	* [3.6 rebase](https://git-scm.com/book/zh/v2/Git-分支-变基) 一种更高级的合并方法，一下看不懂的可以放放；看不懂的时候尽量别用，滥用产生的副作用很大！

		- 确保在向远程分支推送时能保持提交历史的整洁
		- `变基的风险` 不要对在你的仓库外有副本的分支执行变基
		- `变基 vs. 合并` 总的原则是，只对尚未推送或分享给别人的本地修改执行变基操作清理历史，从不对已推送至别处的提交执行变基操作，这样，你才能享受到两种方式带来的便利

- [功能分支工作流 by Git](https://github.com/oldratlee/translations/blob/master/git-workflows-and-tutorials/workflow-feature-branch.md)
- [Github 跨 Repository 开发流程](http://www.ruanyifeng.com/blog/2015/08/git-use-process.html) @阮一峰 2015年8月5日 Gitflow 工作流