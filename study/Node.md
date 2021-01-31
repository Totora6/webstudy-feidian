# 0. 命令行操作

1. 按Tab键可自动补齐文件名
2. shift+鼠标右键快捷切到PowerShell
3. VSC中可安装Terminal插件，快速在vsc的cmd中固定至相应文件夹
4. cmd中，cd xxx表示进入下一级xxx菜单
5. cmd中，cls表示清屏
6. cmd中，按下上箭头可以自动输入上次输入的内容
7. cmd中，ctrl+C退出服务器
8. cmd中，cd..表示退到上一层文件夹
9. cmd中，ipconfig可以查询IP地址
10. Win+R运行，输入mspaint，打开画图
11. i+上箭头，返回已经执行过的命令
12. 关闭服务器请求：ctrl+c

# 1. Node.js简介

## 1.0 API是什么：

API是应用程序接口，又称为应用编程接口，是软件系统不同组成部分衔接的约定。

## 1.1 简介

- Node.js® is a JavaScript runtime built on [Chrome's V8 JavaScript engine](https://v8.dev/).
  - Node.js不是一门语言
   - Node.js不是库、不是框架
   - Node.js是一个JavaScript运行时环境
   - 简单点来讲就是Node.js可以解析和执行JavaScript代码
   - 以前只有浏览器可以解析执行JavaScript代码
   - 在Node.js出现之后JavaScript可以完全脱离浏览器来运行
- Node.js uses an event-driven（事件驱动）,non-blocking I/O model （非阻塞I/O模型）that makes it lightweight and efficient.（轻量和高效）
- Node.js package ecosystem,npm,is the largest ecosystem of open source libraries in the world.
- 浏览器中的JavaScript

  - EcmaScript
    - 基本的语法
    - if
    - var
    - function
    - Object
    - Array
  - Bom
  - Dom
- Node.js中的JavaScript
  - 没有Bom、Dom
  - EcamScript
  - 在Node这个JavaScript执行环境中为JavaScript提供了一些服务器级别的操作API
    - 文件读写
    - 网络服务的构建
    - 网络通信
    - http服务器

## 1.2 Node.js能做什么

- Web服务器后台

- 命令行工具

  ​		npm（node）

  ​		git（c语言）

  ​		hexo（node）

  

- 游戏服务器

- 对于前段开发工程师来讲，接触node最多的是它的命令行工具，自己写的很少，主要是使用别人第三开发的

  ​	webpack

  ​	gulp

  ​	npm

## 1.3 预备知识

1. HTML

2. CSS

3. Javascript

4. 简单的命令行操作(参考链接:https://jingyan.baidu.com/article/ceb9fb1074947b8cad2ba0f9.html)

   cd   打开目录

   ​	***切换目录***：***“cd”是打开目录，改变盘符  直接输***

   ***1、从C盘切换到其他盘，D盘、E盘***：***输入“d:”***

   ***2、打开D盘下的某个文件夹***：***输入“cd test”***

   ***3、返回上一级目录***：***输入“cd ..”***

   ***4、回到根目录***：***输入“cd \”***

   dir  查看目录内容

   Is	查看文件的路径

   mkdir	创建目录

   rm	删除文件

https://blog.csdn.net/Double___H/article/details/99853616

# 2. helloworld

1. 创建编写Javascript脚本文件

2. 打开终端定位到脚本文件所属目录

3. 输入`node 文件名  `执行对应的文件

   注意:文件名不要使用node.js来命名

   **解析执行Javascript**

   **读写文件**

   **http**

## 2.1 读取文件

```javascript
// 浏览器中的 JavaScript 是没有文件操作的能力的

// 但是 Node 中的 JavaScript 具有文件操作的能力



// fs 是 file-system 的简写，就是文件系统的意思

// 在 Node 中如果想要进行文件操作，就必须引入 fs 这个核心模块

// 在 fs 这个核心模块中，就提供了所有的文件操作相关的 API

// 例如：fs.readFile 就是用来读取文件的



// 1. 使用 require 方法加载 fs 核心模块

var fs = require('fs')



// 2. 读取文件

//  第一个参数就是要读取的文件路径

//  第二个参数是一个回调函数

//     

//    成功

//     data 数据

//     error null

//    失败

//     data undefined没有数据

//     error 错误对象

fs.readFile('./data/a.txt', function (error, data) {

 // <Buffer 68 65 6c 6c 6f 20 6e 6f 64 65 6a 73 0d 0a>

 // 文件中存储的其实都是二进制数据 0 1

 // 这里为什么看到的不是 0 和 1 呢？原因是二进制转为 16 进制了

 // 但是无论是二进制01还是16进制，人类都不认识

 // 所以我们可以通过 toString 方法把其转为我们能认识的字符

 // console.log(data)



 // console.log(error)

 // console.log(data)



 // 在这里就可以通过判断 error 来确认是否有错误发生

 if (error) {

  console.log('读取文件失败了')

 } else {

  console.log(data.toString())

 }

})
```

## 2.2 读取文件

//第一个参数：文件路径

//第二个参数：文件内容

//第三个参数：回调函数

成功：

​	文件写入成功

​	error 是null

失败：

​	文件写入失败

​	error就是错误对象

**在写的时候注意几点问题：**

- windows+R 打开cmd控制（或者在文件夹下shift+鼠标右键  或者直接在vscode里面使用Terminal）
- 输入 cd+空格 然后再按tab键可以选择目录
- 左后node+空格+要执行的js文件

# 3. http

在Node中专门提供了一个核心模块：http

http这个模块的职责就是帮你创建编写服务器的。

1. 加载http核心模块

2. 使用http.creatServe()方法创建一个Web服务器，返回一个Serve实例

3. 服务器要干嘛？--

   提供服务：数据的服务

   发送请求

   接收请求

   处理请求

   给个反馈（发送响应）

   注册request请求事件

   当客户端请求过来时，就会自动触发服务器的request请求事件，然后执行第二个参数：回调处理函数

4. 绑定端口号，启动服务器

   最简单的http服务

![image-20200806214417352.png](https://i.loli.net/2021/01/31/TxWn1IewRMFfzJ7.png)

```javascript
var http = require('http')
var serve = http.createServer()
serve.on('request',function(){
    console.log('收到客户的请求了');
})
serve.listen(3000,function(){
    console.log('服务器启动成功了，可以通过http://127.0.0.1:3000/来进行访问')
})
```

## 3.1 发送响应

request 请求事件处理函数，需要接收两个参数：

​	Request 请求对象 

​		请求对象可以用来获取客户端的一些请求信息，例如请求路径	Request 响应对象 

​		响应对象可以用来给客户端发送响应消息

request对象有一个方法：write 可以用来给客户端发送响应数据，其中write可以使用多次，但是最后一定要使用end来结束响应，否则客户端会一直等待。

**http根据不同的路径返回不同的数据步骤：**

1. 创建Serve
2. 监听request请求事件，设置请求处理函数
3. 绑定端口号，启动服务

## 3.2 端口号

**端口号的定义**：所谓的端口，就好像是门牌号一样，客户端可以通过ip地址找到对应的服务器端，但是服务器端是有很多端口的，每个应用程序对应一个端口号，通过类似门牌号的端口号，客户端才能真正的访问到该服务器。为了对端口进行区分，将每个端口进行了编号，这就是端口号。

FTP：文件传输协议

**查看端口号：**

1. 利用系统内置的命令： netstat       或者         netstat -n
2. 利用第三方端口扫描软件



# 4. Node中的Javascript

- EcmaScript
- 核心模块
- 第三方模块
- 用户自定义模块

## 4.1 核心模块

Node为JavaScript提供了很多服务器级别的API，这些API绝大多数都被包装到了一个具名的核心模块中。例如：文件操作的`fs`核心模块，http服务构建的`http`模块，`path`路径操作模块，`os`操作系统信息模块。

以后只要说这个模块是一个核心模块，就必须：

```javascript
var fs = require('fs')
var http = require('http')
```

## 4.2 用户自定义模块

- require
- exports

# 5. Web服务器开发

## 5.1 IP地址和端口号的概念

- IP地址：用来定位计算机
- 端口号：用来定位具体的应用程序
- 所有需要联网通信的应用程序都会占用一个端口号
- 端口号的范围从0~65536之间
- 在计算机中有一些默认端口号：例如，http服务的80
- 可以同时开启多个服务，但一定要确不同服务占用的端口号不一致。即在一台计算机中，同一端口号同一时间只能被一个程序占用。

## 5.2 不同类型的Content-type

参考链接：https://tool.lu/			https://tool.oschina.net/

图片不需要指定编码(即去掉charset=utf-8)，因为我们常说的编码一般指的是：字符编码。 

## 5.3 SEO：搜索引擎优化

Search Engine Optimization

搜索引擎优化是一种利用搜索引擎的搜索规则来提高目的网站在有关搜索引擎内的排名的方式。

# 6. 代码风格

为了约定大家的代码风格，所以在社区中诞生了一些比较规范的代码风格规范：

- [IavaScript Standard Style](https://standardjs.com/)

- [Arbnb JavaScript Style](https://www.ctolib.com/mip/getjll-JavaScript-Style-Guide.html)

  ## 代码无分号问题

  一般情况下是可以不加的，但是要注意几种情况：

  - 当采用了无分号的代码风格时，只需要注意以下三种情况就不会有问题了：

    - 当一行代码是以：

      （

      [

      、

      开头的时候，则在前面补上一个分号用以避免一些语法解析错误。

# 7. npm

参考链接： https://www.npmjs.com/

node package manager

## 7.1 npm命令行工具

npm的第二层含义就是一个命令行工具，只要安装了node,就已经安装了npm。npm也有版本这个概念，可以在命令行中输入：

```javascript
npm --version
```

升级npm:

```javascript
npm install --global npm
```

## 7.2 常用命令

- npm init
  - ​	npm init-y  可以跳过向导，快速生成
- npm install
  -   一次性把dependencies 选项中的依赖项全部安装
  -   npm i（简写）
- npm install 包名
  -  只下载
- npm install --save 包名
  - 下载并且保存依赖项（package.json文件中的dependencies选项）
  - npm i-S 包名（）

- npm uninstall 包名
  -  只删除。如果有依赖项会依然保存

- npm uninstall --save 包名
  -  删除的同时也会把依赖信息去除

- npm help
  -  查看使用帮助

- npm 命令 --help
  -  查看指定命令的使用帮助

## 7.3 解决npm被墙问题

npm存储包文件的服务器在国外，有时候会被墙，速度很慢，所以我们需要解决这个问题。

https://developer.aliyun.com/mirror/NPM?from=tnpm

安装淘宝的cnpm:

```shell
# 在任意目录执行都可以
# --global 表示安装到全局，而非当前目录，不能省略，否则不管用
npm install --global cnpm
```

接下来安装包的时候把之前的npm替换成cnpm

举个例子：

```shell
# 这里还是走国外的npm 服务器，速度比较慢
npm install jquery

# 使用cnpm 就会通过淘宝的服务器来下载jquery
cnpm install jquery
```

如果不想安装cnpm 又想使用淘宝的服务器来下载：

```shell
npm install jquery --registry=https://registry.npm.taobao.org
```

但是每一次手动这样加参数很麻烦，所以我们可以把这个选项加入配置文件中：

```shell
npm config set registry https://registry.npm.taobao.org
# 查看npm 配置信息
npm config list
```

只要经过了上面的命令配置，则以后所有的npm install 都会默认通过淘宝的服务器来下载。

# 8.express

官网首页：http://expressjs.com/

