使用前提：Gitblit仓库已经在服务器上搭建成功，并显示首页(gitblit首页.png)以及掌握Git相关知识
首次登录的用户名为admin密码为admin，登录成功后我们就可以管理用户和管理版本库。

1、新建版本库：如图(新建版本库.png)是我新建的版本库，创建好一个空的版本库(空版本库.png)
	使用git clone ssh://admin@xx.xx.xx.xx:29418/new/hellowrold.git命令克隆空库

	//提交版本库信息
	git commit -m "create project"

	//通过命令行推送一个已存在的版本库
	git remote add origin ssh://admin@xx.xx.xx.xx:29418/new/hellowrold.git
	git push -u origin master

	//创建develop分支并推送到远端
	git checkout -b develop remotes/origin/master
	git push -u origin develop

	//创建一个本地分支
	git checkout -b l_develop develop
至此版本库创建完成。

2、给用户分配访问版本库权限

