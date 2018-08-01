## 1.Linux
      
- 如何模拟Linux
    - 我们需要通过gitBash工具模拟Linux [下载地址](http://git-scm.com/download/win)
    - Linux安装
        - CentOS发行版：sudo yum install git
        - Ubuntu发行版：sudo apt-get install git
    - Mac安装
        - 打开Terminal直接输入git命令，会自动提示，按提示引导安装即可。

## 2.Shell 
   - 什么是shell
        - Shell俗称壳，用来区别于Kernel（核），是指“提供使用者使用界面”的软件（命令解析器）。
        它类似于DOS下的command和后来的cmd.exe。它接收用户命令，然后调用相应的应用程序。
   -  shell分类
        - 图形界面shell: 通过提供友好的可视化界面，调用相应应用程序，
        如windows系列操作系统，Linux系统上的图形化应用程序GNOME、KDE等。
        - 命令行shell：通过键盘输入特定命令的方式，调用相应的应用程序，
        如windows系统的cmd.exe、Windows PowerShell，Linux系统的Bourne shell ( sh)、Bourne Again shell ( bash)等
   - shell命令: 就是围绕增删查改
        -  pwd (Print Working Directory) 查看当前目录
        -  cd (Change Directory) 切换目录，如 cd /etc
        -  ls (List) 查看当前目录下内容，如 ls -al,“.”(表示当前目录)和“..”(表示当前目录的父目录)。
        -  mkdir (Make Directory) 创建目录，如 mkdir blog
        -  touch 创建文件，如 touch index.html
        -  echo >>追加文件 >重新添加一行
        -  wc (Word Count) 字数信息统计，如 wc index.html
        -  cat 查看文件全部内容，如 cat index.html
        -  more less 查看文件，如more /etc/passwd、less /etc/passwd  不用学习
        -  rm (remove) 删除文件，如 rm index.html、rm -rf  blog
        -  rmdir (Remove Directory) 删除文件夹，只能删除空文件夹，不常用
        -  mv (move) 移动文件或重命名，如 mv index.html ./demo/index.html
        -  cp (copy) 复制文件，cp index.html ./demo/index.html
        -  head 查看文件前几行，如 head -5 index.html
        -  tail 查看文件后几行 –n –f，如 tail index.html、tail -5 index.html 
        -  history 查看操作历史
        -  whoami 查看当前用户
 
    
## 3.Git命令
- 01.Git初次使用添加用户名和邮箱 
    - 配置用户名：` git config --global user.name "你的用户名" `
    - 配置邮箱  ：` git config --global user.email "你的邮箱" `
    - 删除错误配置  ：` git config --global --unset   "错误的key删除掉" `
    - 查看配置  ：` git config --list `


- 02.查看当前目录文件的状态
    - 命令  : ` git status ` : 查看当前工作目录的状态，是已经放到暂存区，还是提交到仓库了。
    - 或命令: ` git status -s ` 查看简要的状态信息
   
- 03.将文件添加到暂存区
    - 命令: ` git add ./file.txt`:将当前目录中的file.txt添加到暂存区
    - 或者: ` git add .`: 表示将当前目录所有文件都添加的暂存区.
    - 可以对文件执行多次add命令，都会把最新的修改添加到暂存，但是，后页面执行add命令，会把前面执行add命令添加到暂存区的文件覆盖(相同的文件会覆盖)
   
- 05.将文件添加到仓储中
    - 命令  : ` git commit -m "这次我添加了一个变量" `
    - 或命令: ` git commit -m  -c`
     
- 06.查看日志
    - 命令:`git log`
    - 或命令:`git log --oneline`
    - 以图形化查看:`git log –graph`
 
- 07.忽略文件
    - 需要新建一个名为:  .gitignore 的文件
    - 这个文件话.git同级目录.
    - 该文件用来告诉我们的git哪些文件不要被添加一仓储中。
    - 忽略某个目录:  /node_modules
    - 忽略某个文件:  /css/my.css
    - 忽略某一类文件:  /css/*.css
    - 忽略目录下所有文件:  *.*
    - 忽略所有名为node_modules的目录:  node_modules
    - \#号表示注释
       
- 08.版本回退
    - `git reset --hard Head`
        - 回到最近一次提交的版本的文件状态
        - git指向的是上一次提交
    - `git reset --hard Head` 表示回到最近往前第二次的提交'
        - Head后面的^表示回退到第几次
    - `git reset --hard Head1`
    - 表示回到最近一次提交的前一次提交.
    - Head~2,回退到最近一次提交的前2次提交. 
    - 命令: `git reset --hard [版本号]`
    - 示例: `git reset --hard 12dad211` 
    - 回退到某个具体的版本。
    - 可以配合git reflog命令查看历史操作来进行回退 
    - 这里进行版本回退，并不会对文件进行真实的删除
    - 通过git reflog 可以查看到每一次对版本的切换来提交。

- 09.创建Git分支，并切换分支
    - 正在做功能呢，才做了一半，但是为了不丢失代码要提交，又不能影响别人工作。
    - `git branch`: 查看有多少分支
    - `git branch dev`: 创建了一个名为dev的分支
    - `git checkout dev`: 切换到dev分支
    - `git checkout -b dev`: 创建并切换到指定分支

- 10.取消文件版本跟踪
    - git rm --cached readme1.txt    删除readme1.txt的跟踪，并保留在本地。
    - git rm --f readme1.txt    删除readme1.txt的跟踪，并且删除本地文件。
    - 然后git commit即可。但是git status查看状态时还是会列出来。
     
- 合并Git分支
    - `git merge dev` 表示将当前分支与dev分支合并.  
    - `git branch -d dev` 不要在dev分支执行这个命令，在别的的分支执行.
    - `git ls-files -u` 查看冲突未处理的文件列表

- 如果我对某文件进行了修改，但我不想要push到远程仓库，同时我又想获取最新的修改记录

    ```markdown
        git stash save
        git pull --rebase
    ```
    
- 如果暂存内容现在不想在当前分支恢复了，而是想单独起一个分支

    ```markdown
        git stash branch [newBranchName]
    ```

- 想要查看当前工作区与暂存状态内容区别
   ```markdown
        git stash show -p stash{0}
   ```

- 本地代码已经commit后，解决与远程代码冲突问题
    ```markdown
    
        # 获取远端库最新信息 【分支名称】
        git fetch origin [master]
    
        # 做比较
        git diff [本地分支名] origin/[远程分支名]
    
        # 拉取最新代码，同时会让你merge冲突
        git pull
    ```
   
- 和远程仓库关联
    ```markdown
        git init
        git add .
        git commmint -m 'init'
    
        将本地的仓库关联到github上
        git remote add origin https://github.com/luogeger/...
        
        上传github之前，要先pull一下
        git pull origin master
        
        最后push到远程仓库
        git push -u origin master
    ```



# 5.Git流程
- git clone
    - 命令:'git clone [仓储地址]' 如果不需要下载整个仓储，只需要最新的一次提交,加上参数--depth
    - 登录: 直接通过账号密码登录，太麻烦了,通过SSH登录，不用在输入用户名和密码
        - 1.在任意位置输入 ssh-keygen -t rsa 创建rsa密钥
        - 2.将rsa密钥给网站
        - 3.选clone路径的时候选择ssh登录
- push（推送）
    - `git push [地址] master`
    - `git push origin master`
- pull（拉回)
    - `git pull [地址] master`
    - `git pull origin master`
- remote命令使用
    - git remote add “主机名称” “远程仓库地址”添加远程主机，即给远程主机起个别名，方便使用
    - git remote rm“主机名称” 命令用于删除远程主机。
    - git remote 可以查看已添加的远程主机
    - git remote show “主机名称”可以查看远程主机的信息

## 6.GitLab网上使用
- 获取仓库内容
	- git pull 地址/origin master  
	可以通过https地址获取仓库数据，但是这样做太麻烦了，使用origin相当于替换了之前的地址用法都是一样的。
		-  其实这样使用包含了两个操作
		-  git fetch origin (获取远端的分支)
		-  git merge origin/master （合并远端分支）
		
- 远端分支管理
	- 创建远端分支
		- 1.在本地创建好分支以后，本地 push 该分支即可
		- 2.在网页上创建分支好以后，通过git fetch获取该分支
	- 删除远端分支
	    - git push origin --delete 需要删除的分支，那么其他人如果需要更新分支 需要 git fetch -p
	    
- git 补充知识
	- 保存当前的工作现场. https://zhuanlan.zhihu.com/p/28608106
	- 使用git stash保存当前的工作现场，那么就可以切换到其他分支进行工作，或者在当前分支上完成其他紧急的工作，比如修订一个bug测试提交。
	- 查看隐藏分支 git branch -a
	 