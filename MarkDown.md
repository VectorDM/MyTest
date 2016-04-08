hello

ORACLE DB 及 CLIENT AND SQL TOOLS

1. HIS 程序
2. oracle 数据库 （server）
3. plsql (sql tool)
4. sql track 工具（HIS 自带的log）， sql monitor, sql track


Version control tools

1. git, gitk, web git (cgit)
2. git 的安装及使用 （http://192.168.10.200 搜索 git)
3. ssh-keygen创建公钥目录
3. git流程 
   git clone, add, commit, push
   
4.直接返回
	git checkout -- readme.txt
5.add 后返回
    git reset head readme.txt
	git checkout -- readme.txt
6.commit后删除文件
	rm text.txt
	git st
	git rm text.txt
	git commit -m"remove text.txt"
7.删错了版本库里面还有，要恢复
	git checkout -- readme.txt
8.要关联一个远程库，使用命令git remote add origin git@server-name:path/repo-name.git；

	关联后，使用命令git push -u origin master第一次推送master分支的所有内容；

	此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；
9.创建dev分支，然后切换到dev分支
	git checkout -b dev
	相当于两条命令：
	$ git branch dev
	$ git checkout dev
10.返回上一级目录
	cd ..
11.用git branch命令查看当前分支
	git branch命令会列出所有分支，当前分支前面会标一个*号。
12.把dev分支的工作成果合并到master分支上：
	$ git merge dev
13.删除分支
	git branch -d dev
14.解决冲突，查看分支合并情况
	$ git log --graph --pretty=oneline --abbrev-commit
	*   c5e8342 conflict fixed
	|\
	| * e880a5e AND simple
	* | e33f51d & simple
	|/
	* 41d22c6 branch test'
	* 60284d7 remove text.txt
	* 28f56f5 add test.txt
	* 3a8d9c3 changes of files
	* 8700fec git tracks changes
	* f6c7fd2 add LICENSE.txt
	* f4f3ed4 add 3 lines
	* 5830147 append GPL
	* 0137b9c add distributed
	* 2d9620d wrote a readme file
15.分支管理策略
	如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以看出分支信息。
	下面我们实战一下--no-ff方式的git merge：

	首先，仍然创建并切换dev分支：

	$ git checkout -b dev
	Switched to a new branch 'dev'
	修改readme.txt文件，并提交一个新的commit：

	$ git add readme.txt 
	$ git commit -m "add merge"
	[dev 6224937] add merge
	 1 file changed, 1 insertion(+)
	现在，我们切换回master：

	$ git checkout master
	Switched to branch 'master'
	准备合并dev分支，请注意--no-ff参数，表示禁用Fast forward：

	$ git merge --no-ff -m "merge with no-ff" dev
	Merge made by the 'recursive' strategy.
	 readme.txt |    1 +
	 1 file changed, 1 insertion(+)
	因为本次合并要创建一个新的commit，所以加上-m参数，把commit描述写进去。

	合并后，我们用git log看看分支历史：

	$ git log --graph --pretty=oneline --abbrev-commit
	*   7825a50 merge with no-ff
	|\
	| * 6224937 add merge
	|/
	*   59bc1cb conflict fixed
	
	在实际开发中，我们应该按照几个基本原则进行分支管理：

	首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

	那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；

	你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。

	所以，团队合作的分支看起来就像这样：
	http://www.liaoxuefeng.com/files/attachments/001384909239390d355eb07d9d64305b6322aaf4edac1e3000/0

	git-br-policy

	小结

	Git分支十分强大，在团队开发中应该充分应用。

	合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。
16.修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；
	当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场。
17.丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除
   
   
eTop   
http://192.168.23.233



FineReport入门
http://192.168.10.200/it/?p=1417


git上载报表文件
git last --stat		//最后文件
git status		//查询新文件
git add --all
git st
git commit - asm"新文件名"
git pull
rm his/***.cpt		//删除文件


git rm ***.cpt
git commit -m""
git push



his登陆账号密码：
8888
neusoft9680

manager
his

本地git:
Penguin
drunkpenguin@163.com

github上
username：VectorDM
password：905000080hukui
origin：https://github.com/VectorDM/testgit.git




Git基本常用命令如下：

   mkdir：         XX (创建一个空目录 XX指目录名)

   pwd：          显示当前目录的路径。

   git init          把当前的目录变成可以管理的git仓库，生成隐藏.git文件。

   git add XX       把xx文件添加到暂存区去。

   git commit –m “XX”  提交文件 –m 后面的是注释。

   git status        查看仓库状态

   git diff  XX      查看XX文件修改了那些内容

   git log          查看历史记录

   git reset  –hard HEAD^ 或者 git reset  –hard HEAD~ 回退到上一个版本

                        (如果想回退到100个版本，使用git reset –hard HEAD~100 )

   cat XX         查看XX文件内容

   git reflog       查看历史记录的版本号id

   git checkout — XX  把XX文件在工作区的修改全部撤销。

   git rm XX          删除XX文件

   git remote add origin https://github.com/tugenhua0707/testgit 关联一个远程库

   git push –u(第一次要用-u 以后不需要) origin master 把当前master分支推送到远程库

   git clone https://github.com/tugenhua0707/testgit  从远程库中克隆

   git checkout –b dev  创建dev分支 并切换到dev分支上

   git branch  查看当前所有的分支

   git checkout master 切换回master分支

   git merge dev    在当前的分支上合并dev分支

   git branch –d dev 删除dev分支

   git branch name  创建分支

   git stash 把当前的工作隐藏起来 等以后恢复现场后继续工作

   git stash list 查看所有被隐藏的文件列表

   git stash apply 恢复被隐藏的文件，但是内容不删除

   git stash drop 删除文件

   git stash pop 恢复文件的同时 也删除文件

   git remote 查看远程库的信息

   git remote –v 查看远程库的详细信息

   git push origin master  Git会把master分支推送到远程库对应的远程分支上




![][1]
[1]: http://latex.codecogs.com/gif.latex?\prod%20\(n_{i}\)+1