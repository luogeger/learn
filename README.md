
# Learn

https://www.youtube.com/c/PrimitiveTechnology
- PC
	- 1.测试硬盘读写速度
		- 管理员身份打开命令行``winsat disk -drive c``

	- 2.删除嵌套很深的文件夹
		- 假如需要删除的文件夹是nodejs\node_modules\node_modules...
		- 1.在nodejs中同级目录下创建一个临时文件夹 t
		- 2.打开命令行窗口，进入nodejs目录下
		输入命令：C:\Windows\System32\Robocopy.exe /MIR t node_module
		
	- 3.硬件检测 cmd => dxdiag
	
	- 4.用户账户修改 cmd => netplwiz
		- cmd => regedit
			- 计算机\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList
    
## tools
- webstorm
    - 1.webstorm 
    	– 激活 http://idea.imsxm.com 
        - [搭建服务器](http://blog.csdn.net/larennani/article/details/71447150?locationNum=9&fps=1)
        - [help](https://www.jetbrains.com/help/webstorm/meet-webstorm.html)
        - 主题颜色：config/color (gutter, text, FFFBE8, font: Fira Code)
        - plugin
		    - CodeGlance 
		    - key promoter 快捷键提示
		    
- vscode
    - 1.ctrl + F1 : view in browser; "command": "extension.viewInBrowser",
    - 2.自动保存: "files.autoSave": "afterDelay",
    - 3.keyboard: 
    - 4.tab: 
    
    
- chrome
	- C:\Users\luogeger\AppData\Local\Google\Chrome\User Data\Default\Extensions
	- Octotree ：git树结构
	- JSON viewer
	- Markdown Reader
	- Pixlr Editor：在线版Photoshop
	-  Adblock Plus : 去广告插件
	
- skill
	- Chrome变成一个在线IDE, 只要把github地址改成 https://stackblitz.com/github 开头就可以了。
		- https://github.com/gothinkster/angular-realworld-example-app
		- https://stackblitz.com/github/gothinkster/angular-realworld-example-app
		
	- cortana 搜索应用 => PowerShell
		- Get-AppXPackage -Name Microsoft.Windows.Cortana | Foreach {Add-AppxPackage -DisableDevelopmentMode -Register "$($_.InstallLocation)\AppXManifest.xml"}
		

	- Deluminate 这是一个 Chrome 浏览器的插件，可以让任何网站变成 "夜晚模式"。
		
- sortware
 	- ScreenToGif.exe  录制屏幕, 张脑湿，回复gif
	
	- Xnip 方便好用的滚动截图工具。
	
	- Wallpaper Engine 桌面壁纸
	 
## Node

- 什么是Node
  + Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。[官网](https://www.nodojs.org)
  
- 安装Node
  + 不要安装在中文路径
  + nvm Node Version Manager（版本管理）
  + nrm Node Registry Manager（路径管理）
  + npm Node Package Manager （依赖包管理）
    www.npmjs.com npm下载地址
	
- 常用nvm命令
  + nvm ls 查看node下载的版本
  + nvm install 4.6.0 下载名为4.6.0的版本
  + nvm use 4.6.0 切换4.6.0版本
  
  
- 常用nrm 命令
  - ``nrm下载``: ``npm install -g nrm``
  - ``检查``: ``nrm ls``
  - ``切换到cnpm下载源``: ``nrm use cnpm ``
    - **注意：** 有时候npm的速度很慢，可以考虑cnpm, 输入下面命令行
    - ``npm install -g cnpm --registry=https://registry.npm.taobao.org``
    -  输入命令：``cnpm``检查是否安装好，以后用到npm的地方用cnpm代替。
  
- 常用的npm命令
  + npm init 初始化一个	package.json  文件，如果加上-y就不需要在敲回车了
  + npm install -g bower 全局安装bower
  + npm install jquery --save-dev 本地安装jquery并记录到package.json中
  + npm uninstall 包名 删除包 如果是全局安装就加上-g

## block-chain
  - http://static.runoob.com/download/blockchain.pdf
  - http://static.runoob.com/download/2018cnblockchain.pdf 















