* Git 是啥？ 
* 相比 SVN 有什么不同 ？
* 使用 SVN 用的好好的，为什么要用 Git ？


## First, what is Git ?

Git is a free and open source  distributed version control system (SCM) created by Linus Torvalds in 2005 ( Linux OS founder). It is designed to manage everything for small or very large projects with speed and efficiency. Majors organisations like Google, Facebook, Microsoft uses Git daily.

## Git 与 SVN 的不同之处

### 去中心化带来的巨大变化

- 引入本地版本库

	本地开发版本+远端版本库 vs 本地开发版本+本地版本库+远端版本库

- 结构复杂度 + 1， 带来 概念、命令 复杂度增加

- 降低了对远端版本库的依赖，增强了版本管理的可扩展性和性能

	1. 本地管理无需任何授权
	2. 分支、合并操作简便
	3. 支持各种管理流程，扩展性强

### 基于对象方式的管理

- 先进的内容寻址文件系统，所有的历史信息都以对象形式存在本地版本库中

	参考 [Git 内部原理](https://git-scm.com/book/zh/v2/Git-内部原理-底层命令和高层命令)

- 工作目录下只存放当前的版本，干净！

### 一目了然的暂存区(Index)

查看即将提交的内容、进行部分提交等

## Git 相比 SVN 的一些优势

![Git vs SVN](images/why-git.png)

:point_right: *素材主要来自 [@oldratlee](https://github.com/oldratlee) 的 [repo](https://github.com/oldratlee/software-practice-miscellany/blob/master/git/README.md)*

### 1. 历史记录更清晰完整
#### :beer: 合并对提交过程的保留

- `git`：合并操作保留原有的提交过程（即保留了合并来源的作者、提交次数、分离提交的内容）。
- `svn`：合并操作把来源多个提交合并成了一个合并提交，即在提交历史中Crash了自然的提交过程。

保留原有的提交过程，可以无需繁琐追踪历史就方便的

1. 跟踪修改过程。
1. 直接从提交中就可以看到原提交的作者信息，体现了对作者的尊重。
1. 自然的提交过程。这极大方便了代码细节演进过程的查看。
1. 极大方便查出那行提交是什么时间、谁做出的。  
`svn`因为合并Crash了自然的提交过程，要追踪很痛苦。

#### :beer: 可以修正错误的提交

- `git`：可以修正提交。  
使用功能分支工作流，在自己的分支可以方便修正提交而不会影响大家。
- `svn`：一旦提交就到服务器上，实际使用中就是不能修改。  
（`svn`可以在服务器上修改，因为过程复杂需要权限实际上从不会这样做。）

实际使用中会有误提交的情况（如提交了一个不该提交的日志文件），对于`svn`来说，就是让大家一遍又一遍看到这个垃圾文件。

没有干净的提交，严重影响了`Code Review`，增加成本。

另外对于想了解演进过程的同学，垃圾提交影响了了解效果。

### 2. 对协作开发支持更强
协作开发、版本发布更方便，周边系统支持更完备

#### :beer: 廉价好用的本地分支

- `git`：有本地分支
- `svn`：无本地分支

`git`可以方便创建本地分支，且创建分支的时间是`O(1)`，即瞬间就创建好了。由于分支可以是本地的，也就不存在`svn`目录权限的问题。

可以从想要工作点闪电般创建本地分支，本地实验不确定的修改，创建分支如此之廉价，`git`推荐创建分支来隔离修改。

#### :beer: 更强大智能的合并能力

- `git`：重命名（无论文件还有目录）提交 可以合并上 文件重命名前的这些文件的提交。
- `svn`：重命名（无论文件还有目录）提交后，你本地/或是分支上 有文件重命名前的这些文件的修改或提交，在做合并操作时，恭喜:see_no_evil:，你会碰上传说中难搞的***树冲突***！

因为惧怕`svn`***树冲突***，在包名调整（重命名目录）或类名调整（重命名文件）前，我不得不先向一起开发的组员广播：

1. 提交你的修改
1. 暂停相关类的修改
1. 我开始做调整
1. 等我修改好后:scream:，你再开始修改

OMG～ :confounded:～～

因为这个过程烦琐，结果就是影响了大家去做这样重构操作的积极性，进而影响项目的代码质量改进！

别忘了，如果你的项目是开源的，全球的人可以给你提交，可没有办法向全球的同学广播 :kissing:

#### :beer: 原生支持`tag`

- `svn`在模型上是没有分支和`tag`的。`tag`是通过目录权限限制（对开发只读）来保证不变。
- `git`从模型上就支持`tag`，保证只读。

内心是不是有强烈的安全感？ :sparkles:


#### :beer: 完整配套的开发过程设施

与`git`配套的`github`、`gitlab`（我们公司搭建了）提供了：

- `Markdown`：高效的文档编写和查看。
- `Issue` & `Milestone`：问题记录&跟踪，任务分配，版本规划&管理
- `Wiki`系统：体系的文档
- 评论：可以对代码提交（即是Code Review）& Issue做评论。  
这个有记录交流的过程。

记住，上面的一切和代码一起集中管理，是以代码为中心的，可以方便的工程中的代码。

可运行并完成功能的代码（且叫目标代码） 才是整体项目真正生效的产出。

一切不为 目标代码 服务 的东东都是 **流氓**！  
\# 是不是想到很多东西（比如下压式的排期计划）会觉得自己是生效的产出，好像剩下的事就是 码农搬砖一样把代码码好。

### 3. 性能更优

#### :beer: 提交

- `git`提交是个本地操作，相对`svn`闪电一般。
- `git`提供了暂存区，可以方便指定提交内容，而不是全部。  
PS： `git`可以只提交一个文件修改的一部分而非全部（`Git add –p`），使用相对繁琐些。（实际上开发中我很少这么做 :grin:）

这让开发者更愿意整理提交，让每个提交更内聚自包含。进而有利于

- `Code Review`
- 线上`Bug`的快速准确的回滚式修复

#### :beer: 查看日志

查看日志是个频繁的操作。

- `git`：本地包含了完整的日志，闪电的速度（并且无需网络）。
- `svn`：需要从服务拉取。

一旦用了`git`后，等待`svn`日志（包括查看2个版本间的`diff`）过程简直让我发狂。

#### :beer: 存储

Git 版本库所需的存储空间约为 SVN 的1/30



## 参考内容
- [Why is Git better than Subversion?](http://stackoverflow.com/questions/871/why-is-git-better-than-subversion)  stackoverflow 上关于svn和git的区别的讨论，靠前的帖子推荐都细读一下
- [What are the differences between SVN and Git? ](https://help.github.com/articles/what-are-the-differences-between-subversion-and-git/)  github 上通过版本库结构、历史、子项目（submudle）的不同来对比两者
- [Git Svn Comparison](https://git.wiki.kernel.org/index.php/GitSvnComparsion) 最权威的Git SVN 对比说明
- [蒋鑫：为什么 Git 比 SVN 好？](http://www.worldhello.net/2012/04/12/why-git-is-better-than-svn.html) 对 Git 的误解和两者的使用场景