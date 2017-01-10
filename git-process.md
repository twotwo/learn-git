# Git 使用篇

## 参考
- [Git 使用规范流程](http://www.ruanyifeng.com/blog/2015/08/git-use-process.html) @阮一峰 2015年8月5日

## Command List

### git branch - 查看、创建及删除分支

	☞ 'git branch -a'list both remote-tracking branches and local branches.

### git checkout - 切换分支

	☞ 'git checkout' is used to switch branches
	☞ 'git checkout -b' is used to create and then switch branches

### git pull - 抓取远程仓库内容，合并入当前分支

	☞ 'git pull' update for the repository cloned from, 
		   then merge one of them into current branch

### git rebase - [分支整合](https://git-scm.com/book/zh/v2/Git-分支-变基)

	☞ 'git rebase' reapply commits on top of another base tip

## Process

### 第一步：新建分支
首先，每次开发新功能，都应该新建一个单独的分支（参考 [Git 分支管理](git-branch.md)）

	# 获取主干最新代码
	$ git checkout master
	$ git pull

	# 新建一个开发分支myfeature
	$ git checkout -b myfeature

### 第二步：提交分支commit
分支修改后，就可以提交commit了

	$ git add .
	$ git status
	$ git commit --verbose

### 第三步：撰写提交信息

提交commit时，必须给出完整扼要的提交信息，下面是一个范本([提交信息书写规则](git-commit.md))


	Present-tense summary under 50 characters

	* More information about commit (under 72 characters).
	* More information about commit (under 72 characters).

	http://project.management-system.com/ticket/123

第一行是不超过50个字的提要，然后空一行，罗列出改动原因、主要变动、以及需要注意的问题。最后，提供对应的网址（比如Bug ticket）

### 第四步：与主干同步
分支的开发过程中，要经常与主干保持同步

	$ git fetch origin
	$ git rebase origin/master

### 第五步：合并commit
分支开发完成后，很可能有一堆commit，但是合并到主干的时候，往往希望只有一个（或最多两三个）commit，这样不仅清晰，也容易管理。

那么，怎样才能将多个commit合并呢？这就要用到 git rebase 命令。

	$ git rebase -i origin/master

git rebase命令的i参数表示互动（interactive），这时git会打开一个互动界面，进行下一步操作

### 第六步：推送到远程仓库

合并commit后，就可以推送当前分支到远程仓库了

    $ git push --force origin myfeature

git push命令要加上force参数，因为rebase以后，分支历史改变了，跟远程分支不一定兼容，有可能要强行推送

### 第七步：发出Pull Request(Only for Github)

提交到远程仓库以后，就可以发出 Pull Request 到master分支，然后请求别人进行代码review，确认可以合并到master

(End)