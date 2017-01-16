# README
Git团队培训与实践材料，基于Git的协作开发

##目标定位
介绍Git基本使用及团队协作流程，让团队掌握版本管理、代码审核、软件发布等基本开发流程。

*如果你要有一些资源，希望和我一起，把这个搞起来，很简单，`Fork - 修改 - Pull Request` 就 ok。*

## Git 基础

- [Why Git](why-git.md) Git 是什么？ 相比 SVN 有哪些不同？ 为啥要用 Git 替换 SVN ？
- [Pro Git v2 中文版](https://git-scm.com/book/zh/v2) Git 学习参考权威，可以慢慢啃

### 入门
- [工具篇](git-tools.md) Git 协作开发使用到的工具、服务总结
- [入门篇](git-primer.md) Git 基础知识介绍，及一个 **集中式工作流程** 的例子
- [分支篇](git-branch.md) Git 分支模型介绍，及一个 **功能分支工作流** 的例子

### 规范
- [提交信息书写规则](git-commit.md) Git协作开发使用到的工具、服务总结
- [流程篇](git-process.md) Git 开发流程总结

## 基于 Git 的协作开发实践

### 工作流实践
- [A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/) 介绍日常推荐的分支开发模型，基于此模型可以通过这个小游戏来进行学习 [Learn Git Branch](http://pcottle.github.io/learnGitBranching/)
- [Git工作流指南](https://github.com/oldratlee/translations/tree/master/git-workflows-and-tutorials)

	* 集中式工作流： SVN 方式
	* 功能分支工作流
	* Gitflow 工作流： 经典模型，体现了工作流的经验和精髓
	* Forking 工作流： GitHub风格
	* Pull Request 工作流： Bitbucket代码托管服务使用的方式，和GitHub基本一样

[Git-workflow-translations](https://github.com/oldratlee/translations/tree/master/git-workflows-and-tutorials)
- 熟悉的工作流后，你是否也想要在 Github 上与他人一起协同工作？那么问题来了，[Github全程指南-如何高效使用？](how-to-use-github.md)
- [Understanding the GitHub Flow](https://guides.github.com/introduction/flow/index.html) This guide explains how and why GitHub Flow works 简单实用，更好的理解Github的模式。
- [How to undo (almost) anything with Git](https://github.com/blog/2019-how-to-undo-almost-anything-with-git) 撤销一切，汇总各种回滚撤销的场景

## 基于 Gerrit 的代码评审实践
代码评审相关



## 参考资料


### ebooks
- [Pro Git](http://git-scm.com/book/zh/v1) 作者Scott Chacon是 Github 的员工，Git 的布道者，这本书被誉为 Git 学习圣经，中间有好多插图描述的浅显易懂，挺适合详细学习下的，最新英文第二版《[Pro Git (Editon 2)](http://git-scm.com/book/en/v2)》；
- [Git-internals-pdf](https://github.com/pluralsight/git-internals-pdf) 老外写的，很给力，从目录上面包括安装使用以及设计原理都有讲解，有机会看看。Pdf 电子版本直接下载地址 [Git-internals.pdf](ebooks/git-internals.pdf)
- [Git Community Book](http://gitbook.liuhui998.com/) 汇聚了 Git 社区的很多精华,  并对 Git 的对象模型原理等做了解释，可以深入的了解下 Git 原理。pdf电子版本直接下载地址 [Git Community Book.pdf](ebooks/Git Community Book.pdf)
- [Git权威指南](http://book.douban.com/subject/6526452/) 国内版本控制咨询顾问蒋鑫先生的原创书籍，原生中文叙述，更容易理解，查看[作者写书的缘由](http://www.worldhello.net/gotgit/)
- [Git Reference](http://gitref.org/) [中文](http://gitref.org/zh/index.html) 为学习与记忆 Git 使用中最重要、最普遍的命令提供快速翻阅，可作为参考资料
- [Git Magic - a guide from standord](https://github.com/blynn/gitmagic) 斯坦福大学Git学习指南，适合快速入门


### repositoies on github.com

- [有关 git 的学习资料](https://github.com/xirong/my-git) @xirong 整理的 Git 资源的汇总
- [软件实践杂记](https://github.com/oldratlee/software-practice-miscellany) @李鼎(哲良) 整理的SCM相关内容
- [git-recipes](https://github.com/geeeeeeeeek/git-recipes/wiki) @童仲毅 整理翻译的一些优秀文章
- [Git-flight-rules](https://github.com/k88hudson/git-flight-rules) 一些日常使用中的场景，比如提交错了分支、提交时的用户名邮箱不对、丢弃某些提交、未提交的代码直接提交到另外一个分支等等，很实用




