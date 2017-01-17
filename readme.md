# README
Git 培训材料，培养团队掌握基于 Git 的协作开发技能，规范相关开发流程

##目标定位
介绍 Git 基本使用及团队协作流程，让团队掌握版本管理、代码审核、软件发布等基本开发流程。

*如果你要有一些资源，希望和我一起，把这个搞起来，很简单，`Fork - 修改 - Pull Request` 就 ok。*

## Git 基础

- [Why Git](why-git.md) Git 是什么？ 相比 SVN 有哪些不同？ 为啥要用 Git 替换 SVN ？
- 我们用 [Pro Git v2 中文版](https://git-scm.com/book/zh/v2) 作为 Git 学习的参考教材，这是 Git 学习的权威材料，大家要抽出时间看一遍。

## Git 实战
- [工具篇](git-tools.md) Git 协作开发使用到的工具、服务总结
- [入门篇](git-primer.md) Git 基础知识介绍，及一个 **集中式工作流程** 的例子
- [分支篇](git-branch.md) Git 分支模型介绍，及一个 **功能分支工作流** 的例子

### 流程与规范
- [提交信息书写规则](git-commit.md) Git协作开发使用到的工具、服务总结
- [Git工作流指南](https://github.com/oldratlee/translations/tree/master/git-workflows-and-tutorials)

	* 集中式工作流： SVN 方式
	* 功能分支工作流
	* Gitflow 工作流： 经典模型，体现了工作流的经验和精髓
	* Forking 工作流： GitHub风格
	* Pull Request 工作流： Bitbucket代码托管服务使用的方式，和GitHub基本一样

- [A successful Git branching model](http://nvie.com/posts/a-successful-git-branching-model/) 介绍日常推荐的分支开发模型，基于此模型可以通过这个小游戏来进行学习 [Learn Git Branch](http://pcottle.github.io/learnGitBranching/)

### 基于 Gerrit 的代码评审实践
代码评审相关

## 参考资料
- [有关 git 的学习资料](https://github.com/xirong/my-git) @xirong 整理的 Git 资源的汇总
- [软件实践杂记](https://github.com/oldratlee/software-practice-miscellany) @oldratlee 李鼎(哲良) 整理的SCM相关内容
- [git-recipes](https://github.com/geeeeeeeeek/git-recipes/wiki) @童仲毅 整理翻译的一些优秀文章
- [Git-flight-rules](https://github.com/k88hudson/git-flight-rules) 一些日常使用中的场景，比如提交错了分支、提交时的用户名邮箱不对、丢弃某些提交、未提交的代码直接提交到另外一个分支等等，很实用


