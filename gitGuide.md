## Git流程
- git clone
    - `git clone [仓储地址]`
    - 克隆仓库的某个分支 `-dev`
    - 不需要下载整个仓储, 只要最新的一次提交, `--depth`
    - 1.在任意位置输入 ssh-keygen -t rsa 创建rsa密钥N
    - 2.将rsa密钥给网站
    - 3.选clone路径的时候选择ssh登录
- push（推送）
    - `git push [地址] master`
    - `git push origin master`
- pull（拉回)
    - `git pull [地址] master`
    - `git pull origin master`
- remote命令使用
    - `git remote add [主机名称] [远程仓库地址]`添加远程主机，即给远程主机起个别名，方便使用
    - `git remote rm [主机名称]` 命令用于删除远程主机。
    - `git remote` 可以查看已添加的远程主机
    - `git remote show [主机名称]` 可以查看远程主机的信息
    
    
## Git命令
- **config** 配置个人信息
    - ` git config --list`
    - ` git config --global user.name "你的用户名" `
    - ` git config --global user.email "你的邮箱" `
    - ` git config --global --unset "错误的key删除掉"`

- **status** 查看状态
    - `git status ` : 查看当前工作目录的状态，是已经放到暂存区，还是提交到仓库了。
    - `git status -s ` 查看简要的状态信息
     
- **log** 查看日志
    - `git log`
    - `git reflog` ：查看操作历史
    - `git log --oneline`
    - `git log –graph`  

- **stage** 暂存区
    - `git add ./file.txt`:将当前目录中的`file.txt`添加 **到暂存区**
        - `use "git add <file>..." to update what will be committed`
    - `git add .`: 表示将当前目录 **所有文件**都添加的暂存区.
    - `git checkout -- index.html`: 清空暂存区
        - `use "git checkout -- <file>..." to discard changes in working directory`
   
- **commit** 本地仓储
    - `git commit -m "这次我添加了一个变量" `
    - `git commit -m  -c`

- **branch** 分支
    - `git branch`: 查看有多少分支
    - `git branch dev`: 创建了一个名为dev的分支
    - `git checkout dev`: 切换到dev分支
    - `git checkout -b dev`: 创建并切换到指定分支
    - `git merge dev` 表示将当前分支与dev分支合并.  
    - `git branch -d dev` 不要在dev分支执行这个命令，在别的的分支执行.
    - `git ls-files -u` 查看冲突未处理的文件列表
       
- **reset** 版本回退
    - `git reset --hard <Head>` :回退到某个具体的版本。
    - `git reflog`:配合命令查看历史操作来进行回退 
    - `git rm --cached index.txt` 删除`index.txt`的跟踪，并保留在本地。
    - `git rm --f index.txt`     删除`index.txt`的跟踪，并且删除本地文件。

- `.gitignore`忽略文件
    - `.gitignore` 和 `.git`同级目录    
    - `/node_modules` 忽略某个目录
    - `/css/index.css` 忽略某个文件
    - `/css/*.css` 忽略某一类文件
    - `*.*` 忽略目录下所有文件
    - `doc/a.txt`
    - `doc/**/a.txt`
    - `#`号表示注释

- 如果我对某文件进行了修改，但我不想要push到远程仓库，同时我又想获取最新的修改记录
    - `git stash save`
    - `git pull --rebase`
    
- 如果暂存内容现在不想在当前分支恢复了，而是想单独起一个分支
    - `git stash branch [newBranchName]`

- 想要查看当前工作区与暂存状态内容区别
    - `git stash show -p stash{0}`

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

- tip: 查看暂存区和现在的内容的区别
- tip: 已经存在版本库了，但是要批量取消版本跟踪，但是文件不删除，怎么操作   

## GitLab
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
	 
