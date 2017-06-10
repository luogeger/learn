# Learn
[Me](imgs/mmexport1451125082410.jpg)

- 1.测试硬盘读写速度
	- 管理员身份打开命令行``winsat disk -drive c``

- 2.删除嵌套很深的文件夹
	- 假如需要删除的文件夹是nodejs\node_modules\node_modules...
	- 1.在nodejs中同级目录下创建一个临时文件夹 t
	- 2.打开命令行窗口，进入nodejs目录下
		输入命令：C:\Windows\System32\Robocopy.exe /MIR t node_module

- 3.跨域
	- Ajax跨域几种方法：
		- CORS跨域
		- postMessage跨域
		- document.domain同主域，不同子域之间跨域
		- iframe的hash跨域
		- window.name跨域
		- JSONP跨域
		- 后端代理跨域
			- 其中1、2、3、6是最常用的	

## tools
- webstorm
    - 1.webstorm背景色：浅蓝EDFCED，浅黄F5F5D5


- vscode
    - 1.ctrl + F1 : view in browser; "command": "extension.viewInBrowser",
    - 2.自动保存: "files.autoSave": "afterDelay",
    - 3.keyboard: 
    - 4.tab: 
    
## Node

- 什么是Node
  + Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。[官网](https://www.nodojs.org)

- node 只解析ES,像aler()之类的就不能使用了 
  + 加上谷歌V8对js的解析速度大大提高
  + 提供了一些系统级API,比如对文件的操作
  + 其实就是一个js运行环境
  
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
  - nrm ls查看不同的下载源地址
  - nrm use cnpm 切换到cnpm下载源
  - cnpm 替换 npm,以后用到npm的地方就用cnpm -> 执行下面命令：
- **注意：** 有时候npm的速度很慢，可以考虑cnpm, 输入下面命令行
	- ``npm install -g cnpm --registry=https://registry.npm.taobao.org``
	-  输入命令：``cnpm``检查是否安装好，以后用到npm的地方用cnpm代替。
  
- 常用的npm命令
  + npm init 初始化一个	package.json  文件，如果加上-y就不需要在敲回车了
  + npm install -g bower 全局安装bower
  + npm install jquery --save-dev 本地安装jquery并记录到package.json中
  + npm uninstall 包名 删除包 如果是全局安装就加上-g
  

	
## Typora

```html
<thead>
	<tr>
      <th>Code</th>
      <th>Name</th>
      <th>Price</th>
  	</tr>
</thead>
<--! 快捷键是 Ctrl + shift + F , code fences -->
```

**ctrl + B 文字加粗**

- code横线是4个* ，和文字加粗注意区分

****

Ctrl + ？ 切换代码格式，只能显示部分行号

> ctrl + shift + Q 前面有有竖线，而且文字是斜体，code>

#### ctrl + shift + M 数学

$$
<Empty \space Math \space Block>
<每个单词之间的空格要用转移符号\+space>
$$

##### Ctrl + T  表格Table

|这里是|3列|4行|
|:--:|---:|:--:|
|  a    |  s    |   d   |
|    A  |    S  |    D  |
|这里|其实是|4行|



> 1. `first` 
> 2. `second`
> 3. `third`
>    ​

- **``first``** 
- **`second`**
- **``third``**


- 运动员，他的技能是千锤百炼出来的习惯性、技术性、机械性动作。靠的是这种勇气和热血去做出每一次的反应和判断，还有最后的决定。
这就是为什么运动员会死2次，因为他必须埋葬他第一段运动员生涯的性格才可以开启他真正的第二段。



