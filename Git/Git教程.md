1、Git是什么?<br>&emsp;&emsp;Git是目前世界上最先进的分布式版本控制系统。
2、SVN与Git的最主要的区别？<br>&emsp;&emsp;SVN是集中式版本控制系统，版本库是集中放在中央服务器的，而干活的时候，用的都是自己的电脑，所以首先要从中央服务器那里得到最新的版本，然后干活，干完后，需要把自己做完的活推送到中央服务器。集中式版本控制系统是必须联网才能工作，如果在局域网还可以，带宽够大，速度够快，如果在互联网下，如果网速慢的话，就纳闷了。
&emsp;&emsp;Git是分布式版本控制系统，那么它就没有中央服务器的，每个人的电脑就是一个完整的版本库，这样，工作的时候就不需要联网了，因为版本都是在自己的电脑上。既然每个人的电脑都有一个完整的版本库，那多个人如何协作呢？比如说自己在电脑上改了文件A，其他人也在电脑上改了文件A，这时，你们两之间只需把各自的修改推送给对方，就可以互相看到对方的修改了。
3、安装Git<br>&emsp;&emsp;在Linux安装Git
&emsp;&emsp;登录https://git-scm.com/download/linux，官网上有详细的Git各版本Linux安装教程(Linux版本安装.png)
&emsp;&emsp;在Mac OS X上安装Git
&emsp;&emsp;第一种是安装homebrew，然后通过homebrew安装Git，具体方法请参考homebrew的文档：http://brew.sh/(网址.png)。
&emsp;&emsp;第二种就是直接下载.dmg文件进行安装。
&emsp;&emsp;在Windows上安装Git
&emsp;&emsp;直接从官网下载你所需要的版本的.exe文件(Windows下载.png)，完成安装之后，就可以使用命令行的 git 工具（已经自带了 ssh 客户端）了，另外还有一个图形界面的 Git 项目管理工具。在开始菜单里找到"Git"->"Git Bash"，会弹出 Git 命令窗口，你可以在该窗口进行 Git 操作。
&emsp;&emsp;接下里还需要最后一步设置，在命令行输入：
        $ git config --global user.name "Your Name"
        $ git config --global user.email "email@example.com"
		--global 选项，更改的配置文件就是位于你用户主目录下的那个，以后你所有的项目都会默认使用这里配置的用户信息。如果要在某个特定的项目中使用其他名字或者电邮，只要去掉 --global 选项重新配置即可，新的设定保存在当前项目的 .git/config 文件里，使用$ git config --list可以看到你的配置信息。
4、Git的工作流程<br>
	克隆Git项目资源作为工作目录
	在本地对项目进行操作
	如果有人对项目进行更新，你可以更新Git项目资源
	在提交前查看修改
	提交修改
	如果发现错误，可以撤销回交再次确认修改并提交


