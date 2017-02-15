# Gerrit 起步

## 登录 Web 控制台
[Gerrit Web Console](http://172.16.100.90/gerrit/) 已经集成了大家的jira账号，可以直接登录(Sign In)

![Gerrit Sign In](images/gerrit-sign-in.png)

## 配置 SSH(HTTP) 访问认证 

进入[Settings](http://172.16.100.90/gerrit/#/settings/)界面

### SSH Public Keys

![Gerrit SSH Public Keys](images/gerrit-ssh-public-keys.png)

点"Add Key ..."按钮，把本机ssh密钥对中的公钥填入对话框。 

☞ 进一步阅读： [Use Public Key Authentication with SSH](https://www.linode.com/docs/security/use-public-key-authentication-with-ssh)

完成以上配置后，我们就可以与 Gerrit 进行对话了

	➜  learn-git git:(master) ✗ ssh -p29418 liyan@172.16.100.90

	  ****    Welcome to Gerrit Code Review    ****

	  Hi liyan, you have successfully connected over SSH.

	  Unfortunately, interactive shells are disabled.
	  To clone a hosted Git repository, use:

	  git clone ssh://liyan@172.16.100.90:29418/REPOSITORY_NAME.git

	Connection to 172.16.100.90 closed.

### HTTP Password

![Gerrit HTTP Password](images/gerrit-http-password.png)

On Gerrit installations that do not support SSH authentication, the user must authenticate via HTTP/HTTPS.

参考[链接](https://gerrit-documentation.storage.googleapis.com/Documentation/2.13.3/user-upload.html#http)


## 执行一下 `gerrit` 命令

	ssh -p29418 172.16.100.90 gerrit

可以看到这个命令的使用提示信息。为了减少输入，我设置了一个别名

	alias gerrit="ssh -p29418 172.16.100.90 gerrit"

## 创建 Gerrit Project

首先，我们创建一个专用的个人工程，即在远端生成一个 git 仓库

	➜  learn-git git:(master) ✗ gerrit create-project users/liyan

然后，我们把这个工程 `clone` 到本地

	➜  /tmp git clone ssh://172.16.100.90:29418/users/liyan
	Cloning into 'liyan'...
	warning: remote HEAD refers to nonexistent ref, unable to checkout.

⚠️因为仓库是空的，所以有一个警告

## 设置 Gerrit Change-Id

为实现 Review 的功能，我们需要在 git 中添加一个标识提交信息唯一性的钩子

	➜  /tmp cd liyan 
	➜  liyan git:(master) curl -Lo .git/hooks/commit-msg http://172.16.100.90/gerrit/tools/hooks/commit-msg
	  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
	                                 Dload  Upload   Total   Spent    Left  Speed
	100  4682  100  4682    0     0   278k      0 --:--:-- --:--:-- --:--:--  285k
	➜  liyan git:(master) chmod u+x .git/hooks/commit-msg
	➜  liyan git:(master) more .git/hooks/commit-msg

## Submit changes for review

	➜  liyan git:(master) ✗ git add readme.md 
	➜  liyan git:(master) ✗ git commit -m 'first commit'
	[master (root-commit) b428baa] first commit
	 1 file changed, 51 insertions(+)
	 create mode 100644 readme.md
	➜  liyan git:(master) git log 
	commit b428baa82a90fb8889fd361a760859eb20c96d97
	Author: twotwo <twotwo.li@gmail.com>
	Date:   Wed Feb 15 12:13:18 2017 +0800

	    first commit
	    
	    Change-Id: I54bd083f502906705d565c52898307804ded0358
	(END)

	## Verify Changes
	## Submit the Change
	➜  liyan git:(master) git push -u origin master
	Counting objects: 3, done.
	Delta compression using up to 8 threads.
	Compressing objects: 100% (2/2), done.
	Writing objects: 100% (3/3), 2.12 KiB | 0 bytes/s, done.
	Total 3 (delta 0), reused 0 (delta 0)
	remote: Processing changes: refs: 1, done    
	To ssh://172.16.100.90:29418/users/liyan.git
	 * [new branch]      master -> master
	Branch master set up to track remote branch master from origin.