# 协作开发与持续集成
.notes: Generate HTML5 slideshows by landslide

<!-- landslide index.md --relative --copy-theme -d index.html -->

 * V1.0
 * liyan 2017-11-15

## 从前，有一枚野生的程序猿，加入了一支攻城狮团队 …

<!-- .qr: 450|http://172.16.100.90:10000/slide/gerrit/ -->
![QR Code](images/qr-code.png)

---

## 怎样快速成为一只合格的攻城狮呢？
.notes: 要成为一只合格的攻城狮，小白需要掌握以下内容

* 了解协作开发与持续集成的基本概念 本篇文章
* 学习如何在Windows下[使用 Git Bash](./git-bash.html) 
* 学习更多 gerrit 进行协作开发的知识 [Gerrit 使用入门](./gerrit.html)
* 持续集成练习


---

## 本文主要内容

### 1. 环境介绍
### 2. Gerrit与代码评审
### 3. 持续集成的实践
### 4. 总结

---

## 1. 环境介绍

* 开发机： 攻城狮的生产工具，一般都还是安装的Windows系统
* 测试服务器： 若干安装CentOS的服务器，用来测试服务，团队范围内公用
* 生产服务器： 也叫业务服务器，操作要谨慎！
* Jenkins： 团队的CI服务器，用来支持持续集成流程；
* Gerrit： 团队代码仓库和代码评审平台；

![CI Overview](images/ci_overview.png)

---

## 1.1 开发流程： 从开发到发布

![Jenkins Process](images/git-jenkins-process.png)

---

## 2. Gerrit与代码评审

* Gerrit Web 控制台
* 代码评审

---

## 2.1 Gerrit Web 控制台

### 登录 Web 控制台
[Gerrit Web Console](http://172.16.100.130/gerrit/) 已经集成了账号管理系统，大家可以使用自己的jira账号直接登录(Sign In)

点击Gerrit 页面右上角“Sign In”链接后，出现如下登录界面

![Gerrit Sign In](images/gerrit-sign-in.png)

---

## 3. 持续集成实践

示例

---

## 4. 总结

