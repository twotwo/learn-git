# README
Git 培训材料，培养团队掌握基于 Git 的协作开发技能，规范相关开发流程

##目标定位
介绍 Git 基本使用及团队协作流程，让团队掌握版本管理、代码审核、软件发布等基本开发流程。

*如果你要有一些资源，希望和我一起，把这个搞起来，很简单，`Fork - 修改 - Pull Request` 就 ok。*

## 1、Git 起步

- [Why Git](why-git.md) Git 是什么？ 相比 SVN 有哪些不同？ 为啥要用 Git 替换 SVN ？
- [工具篇](git-tools.md) Git 协作开发使用到的工具和服务
- [入门篇](git-primer.md) Git 基础知识介绍，及一个 **集中式工作流程** 的例子

### 起步 - 总结
读完本章，你应该基本了解 Git 是什么、与集中式版本控制系统有何区别等问题；
并且有了一份能够工作的 Git 版本。

接下来我们将学习 Git 的杀手级特性：分支模型，并以此为基础的其余版本管理工作流。

我们用 [Pro Git v2 中文版](https://git-scm.com/book/zh/v2) 作为 Git 学习的参考教材，这是 Git 学习的权威材料，大家要抽出时间看一遍。

## 2、Git 工作流

- [Git 分支](git-branch.md) Git 分支模型介绍，及一个 **功能分支工作流** 的例子
- [Gitflow 工作流](workflow-gitflow.md) 经典模型，体现了工作流的经验和精髓。裁剪后可以适用于各种规模的企业以及开源项目开发
- [Forking 工作流](workflow-forking.md) GitHub风格，开源项目的理想工作流，适用于松散组织的团队

### 工作流 - 总结
本周讲解了 Git 分支与合并的基础知识。 你现在应该能自如地创建并切换至新分支、在不同分支之间切换以及合并本地分支。
在了解了这几种基本工作流后，根据当前开发特点总结出团队代码管理模式

更全面的理解Git 工作流，推荐阅读[Comparing Workflows](https://www.atlassian.com/git/tutorials/comparing-workflows/) atlassian的 Git 工作流对比，这里还有@oldratlee 的[译文](https://github.com/oldratlee/translations/tree/master/git-workflows-and-tutorials)

* `Centralized Workflow` **集中式工作流** ，用和 SVN 类似的方式完成代码管理
* `Feature Branch Workflow` **功能分支工作流** 是 Git 的基础工作流，是企业项目工作流、开源项目工作流的核心子流程
* `Gitflow Workflow` **Gitflow 工作流** 是 Git 应用中最经典的模型，体现了工作流的经验和精髓
* `Forking Workflow` **Forking 工作流** 是 GitHub 的风格，开源项目的理想工作流，适用于松散组织的团队

## 3、基于 Gerrit 的代码评审实践
代码评审相关

## 4、其它
- [提交信息书写规则](git-commit.md) Git协作开发使用到的工具、服务总结
- [有关 git 的学习资料](https://github.com/xirong/my-git) @xirong 整理的 Git 资源的汇总，[xirong](http://www.ixirong.com/about/){:target="_blank"} 是一位阿里前端/全站工程师
- [软件实践杂记](https://github.com/oldratlee/software-practice-miscellany) @oldratlee 李鼎(哲良) 整理的SCM相关内容
- [git-recipes](https://github.com/geeeeeeeeek/git-recipes/wiki) @童仲毅 整理翻译的一些优秀文章
- [Git-flight-rules](https://github.com/k88hudson/git-flight-rules) 一些日常使用中的场景，比如提交错了分支、提交时的用户名邮箱不对、丢弃某些提交、未提交的代码直接提交到另外一个分支等等，很实用


