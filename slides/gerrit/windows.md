# Git BASH 上手
.notes: Generate HTML5 slideshows by landslide

 * V1.0
 * liyan 2017-11-15

## 从前有个工程师，想用 git …

<!-- .qr: 450|http://172.16.100.90:10000/slide/gerrit/ -->
![QR Code](images/qr-code.png)

---

## 小王的工作环境

* 用一台windows开发机；
* 用一台centos测试机；
* Jenkins
* gerrit

## 小王的学习计划

* 在开发机上安装 git 环境
* 在本地仓库中管理项目
* 使用 gerrit 同步仓库
* 在测试机上同步测试

## 怎样上手呢？

.notes: Git BASH - git for windows

---

## # Git for Windows

Git for Windows是Git官方提供的Windows版本，包括命令行和图形界面。

[git-for-windows](https://git-for-windows.github.io/)

![示意图](https://git-for-windows.github.io/img/gw1web_thumb.png)

---

## 安装
a. Adjusting your PATH environment: Use Git and optional Unix tools
	![add-unix-tools-to-path](images/git-bash-add-unix-tools-to-path.png)

---
## 安装
b. Configuring the line ending conversions: checkout as-is, commit Unix-style line endings
	![checkout-and-commit-unix-style](images/git-bash-checkout-and-commit-unix-style.png)

---
## 安装
c. Configuring the terminal emulator to use the Git Bash: Use Windows' default console window
	![use-windows-console](images/git-bash-use-windows-console.png)

---
## 安装
d. Configuring extra options: 
	* Enable file system caching
	* Enable Git Credential Manager
	![extra-options](images/git-bash-extra-options.png)

---
## 配置
a. 配置访问密钥对

	$ ssh-keygen -q -t rsa -C "testtest@feiliu.com"
	Enter file in which to save the key (/c/Users/liyan/.ssh/id_rsa):
	Enter passphrase (empty for no passphrase):
	Enter same passphrase again:

	liyan@hummer MINGW32 ~/.ssh
	$ ll ~/.ssh/
	total 9
	-rw-r--r-- 1 liyan 197121 1679 Nov 24 17:10 id_rsa
	-rw-r--r-- 1 liyan 197121  401 Nov 24 17:10 id_rsa.pub
	-rw-r--r-- 1 liyan 197121  627 Jun 12  2014 known_hosts


---
## 配置
b. 获取访问用的公钥

	$ cat ~/.ssh/id_rsa.pub
	ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDGIzTh6BKYWI1AjKeTvvsAQm/bxL6iJ9tFXiXnqjXx
	MGDIfno8JMi6CAX0IUC1tj7G1jNuQsmKi2E7P+Ql5SXHIJpboTk8UGqzVq62GOZTaZTV5oZ9TUgMyTv2
	n51jP0T7W9J+0R8g7zneQfFZtKZ0ryCDRCxweZNGFYWku96bBvBYDRiqG/3bbmAh3NRvWx5zKBv6ieat
	gjZpxNaVR0kwd2XX19rFTu4FFDE4RCuKQFlFUVM7uyhvDRWAsha87mitW2WD4xIKVcTzwOmBrGMPOKiv
	FfM3TzkUn0eTFOhJi0U6ynmH7uHAuVHhXWMGmbtWN9e8G8ba82beNPPtMugT testtest@feiliu.com

---
## 配置
c. 把公钥配置到github后台
	![github-new-sshkey](images/github-new-sshkey.png)

---
## 配置
d. 测试访问

	$ ssh -T git@github.com
	Hi twotwo! You've successfully authenticated, but GitHub does not provide shell access.

---

## git bash
推荐*Git for Windows*是为了让大家能在windows的终端下书写命令行。

这里有一篇参考文章[初学git：用git bash往github push代码](http://www.cnblogs.com/zichi/p/4703999.html)
