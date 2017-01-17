# Git 入门篇
- `Git Overview` 概览，介绍 Git 的一些基本概念
- `Centralized Workflow` 一个用集中式工作流程工作的例子，从config、init/clone、commit到push、pull，介绍在使用 Git 中需要掌握的命令

## Git Overview

### Git项目的目录结构
![Git Areas](images/git_areas.png)

一个本地的 Git 项目可以分成三个区域

* Git 仓库(Repository) 			.git目录。保存项目的元数据和对象数据库的地方
* 工作目录(Working Directory)	对项目的某个版本独立提取出来的内容，文件夹中除去.git的其他文件
* 暂存区域(Staging Area)		.git/index文件，也被称作“索引”

### 本地文件的三种状态
本地文件可能处在以下三种状态

* 已提交（committed）文件已经保存到本地Repository中
* 已修改（modified） 文件中的数据相对Repository已经发生了变化
* 已暂存（staged）   对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中

![File Lifecycle](images/file_lifecycle.png)

文件的状态变化周期说明

## Centralized Workflow
![Git Actions](images/git_actions.jpg)

### 账号配置
参考1 [初次运行 Git 的配置](https://git-scm.com/book/zh/v2/起步-初次运行-Git-前的配置)

参考2 [Git 设置和取消代理](https://gist.github.com/laispace/666dd7b27e9116faece6)

参考3 [Git 设置编辑器](https://help.github.com/articles/associating-text-editors-with-git/)

#### git config
	$ git help config

	### Set Your Identity
	$ git config --global user.name "twotwo"
	$ git config --global user.email twotwo@li3huo.com

	### Set/Unset Your Proxy: http&https
	$ git config --global http.proxy 'socks5://127.0.0.1:1080'
	$ git config --global --unset http.proxy

	### Use Sublime as Your Editor
	$ ln -s "/Applications/Sublime Text 2.app/Contents/SharedSupport/bin/subl" ~/app/bin/
	$ git config --global core.editor "subl -n -w"


### 获取与创建项目
参考[Git 获取与创建项目](https://git-scm.com/book/zh/v2/Git-命令-获取与创建项目)

*创建项目* 运行 git init 就可以将一个目录转变成一个 Git 仓库，这样就可以开始对它进行版本管理了
#### git init

	➜  w2016 mkdir scm
	➜  w2016 cd scm
	➜  scm git init
	Initialized empty Git repository in /opt/local/ide/workspaces/w2016/scm/.git/

*获取项目*
#### git clone & git commit

	$ git clone https://github.com/twotwo/learn-git.git
	$ git remote -v            
	origin	https://github.com/twotwo/learn-git.git (fetch)
	origin	https://github.com/twotwo/learn-git.git (push)

### 提交

*检查变更情况*
#### git status

	$ git status
		modified:   primer.md

#### git add

	$ git add primer.md

#### git commit

	$ git commit -m "update primer.md"
	[master 85c4f11] update primer.md
	 1 file changed, 24 insertions(+), 7 deletions(-)
	

### Pushing to Remote

#### git remote

	➜  scm git:(master) ✗ git remote -v
	➜  scm git:(master) ✗ git remote add origin https://github.com/twotwo/scm.git


### 参考
* [一个初始化、提交和同步的例子](http://wiki.eclipse.org/EGit/Git_For_Eclipse_Users#Worked_example) 
* [集中式工作流 by Git](https://github.com/oldratlee/translations/blob/master/git-workflows-and-tutorials/workflow-centralized.md)
