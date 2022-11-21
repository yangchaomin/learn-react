<!-- MarkdownTOC autoanchor="true" autolink="true" -->

- [learn-react](#learn-react)
    - [前言 第一次提交](#%E5%89%8D%E8%A8%80-%E7%AC%AC%E4%B8%80%E6%AC%A1%E6%8F%90%E4%BA%A4)
        - [配置 使用personal access token](#%E9%85%8D%E7%BD%AE-%E4%BD%BF%E7%94%A8personal-access-token)
        - [Github 提交代码很慢、超时](#github-%E6%8F%90%E4%BA%A4%E4%BB%A3%E7%A0%81%E5%BE%88%E6%85%A2%E3%80%81%E8%B6%85%E6%97%B6)
        - [添加忽略文件](#%E6%B7%BB%E5%8A%A0%E5%BF%BD%E7%95%A5%E6%96%87%E4%BB%B6)
        - [目录生成](#%E7%9B%AE%E5%BD%95%E7%94%9F%E6%88%90)
    - [Learn React](#learn-react-1)
        - [JSX](#jsx)
        - [函数式、类式 组件](#%E5%87%BD%E6%95%B0%E5%BC%8F%E3%80%81%E7%B1%BB%E5%BC%8F-%E7%BB%84%E4%BB%B6)
        - [state 属性](#state-%E5%B1%9E%E6%80%A7)

<!-- /MarkdownTOC -->

<a id="learn-react"></a>
# learn-react
学习React记录
>项目中代码都来自于学习网络上视频或教程，本人前端完全不会从0开始，希望大家都能学有所成。

<a id="%E5%89%8D%E8%A8%80-%E7%AC%AC%E4%B8%80%E6%AC%A1%E6%8F%90%E4%BA%A4"></a>
##### 前言 第一次提交
github 的相关操作也是从0开始学习，第一次提交也是一波三折

1. LibreSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:44

通过百度找到解决方案：
>问题原因 因为 Git 的Http代理的问题，Git支持三种协议： git、ssh、http
本来push的时候应该走ssh隧道的，但是因为设置了http代理，所以就走了http的代理，于是就提交不了了。

解决方案
```bash
git config --global --unset http.proxy
```

2. 报错 remote: Support for password authentication was removed on August 13, 2021.

密码模式被移除了，解决方案有 使用ssh免密登录、使用personal access token，我选择了使用 使用personal access token

<a id="%E9%85%8D%E7%BD%AE-%E4%BD%BF%E7%94%A8personal-access-token"></a>
###### 配置 使用personal access token
登录 github，按照如下路径:
>Settings => Developer Settings => Personal Access Token => Generate New Token  => 填写表格 => Generate token => 复制PAT
**注意是在登录头像下面的 Settings 菜单中，在仓库的 Settings 中是找不到的**
复制生成Token后，因为我已经提交过一次，虽然失败了但是 git 已经记录了密码，需要把之前的记录删掉

>For macOS <br/>
Click on the Spotlight icon (magnifying glass) on the right side of the menu bar. Type Keychain access then press the Enter key to launch the app => In Keychain Access, search for github.com => Find the internet password entry for github.com => Edit or delete the entry accordingly => You are done

详细参考地址：[Message "Support for password authentication was removed. Please use a personal access token instead."](https://stackoverflow.com/questions/68775869/message-support-for-password-authentication-was-removed-please-use-a-personal)

密码就使用复制的 PAT，随后提交中也要使用 PAT 码，跌跌撞撞第一次提交终于成功了！

<a id="%E6%B7%BB%E5%8A%A0%E5%BF%BD%E7%95%A5%E6%96%87%E4%BB%B6"></a>

<a id="github-%E6%8F%90%E4%BA%A4%E4%BB%A3%E7%A0%81%E5%BE%88%E6%85%A2%E3%80%81%E8%B6%85%E6%97%B6"></a>
###### Github 提交代码很慢、超时
在前面操作中 github 经常提示超时，所以需要解决一下，以提高效率，使用切换 Host 方式 最简单快捷，当然有科学上网工具就更好了。
这里借助了：[GitHub520](https://github.com/521xueweihan/GitHub520)

<a id="%E6%B7%BB%E5%8A%A0%E5%BF%BD%E7%95%A5%E6%96%87%E4%BB%B6"></a>
###### 添加忽略文件
新创建 .gitignore 文件 添加忽略文件
```bash
# 忽略node_modules目录
node_modules/
# 忽略Logs
logs
*.log
# 忽略/dist目录，相对.gitignore文件所在目录
/dist
# 忽略.env文件
.env
# 忽略IDE的配置文件
.idea/
.vscode/
*.sw*
```

<a id="%E7%9B%AE%E5%BD%95%E7%94%9F%E6%88%90"></a>
###### 目录生成
README.md 文件提交到github上时 [TOC] 标签没有解析成目录，但是看别人大佬的说明文件都是有目录的<br/>
我当前借助的工具是 Sublime Text，需要安装插件:MarkdownTOC 具体安装方式很多百度一下就能成功了。

* 安装 MarkdownTOC 后重启 Sublime Text，并打开 README.md 文件
* 光标在第一行然后 工具 -> MarkdownTOC -> Insert TOC 就会自动插入目录
* 插入的目录还需 修改让支持 锚点 跳转,在 MarkdownTOC 表中中增加属性
```bash
autoanchor="true" autolink="true"
# 即如下
<!-- MarkdownTOC autoanchor="true" autolink="true" -->
```

* 再次提交 github ，即可看到目录
* 后面新增了结构时在 工具 -> MarkdownTOC -> Update TOC 即可更新目录结构

<a id="learn-react-1"></a>
##### Learn React

<a id="jsx"></a>
###### JSX
1.全称:  JavaScript XML

2.react定义的一种类似于XML的JS扩展语法: JS + XML本质是React.createElement(component,props,...children)方法的语法糖

3.作用: 用来简化创建虚拟DOM

* 写法：
```html
var ele=<h1>Hello JSX!</h1>
```

* **注意1：它不是字符串, 也不是HTML/XML标签**
* **注意2：它最终产生的就是一个JS对象**

4.标签名任意: HTML标签或其它标签

5.标签属性任意: HTML标签属性或其它

6.基本语法规则

* 遇到 <开头的代码, 以标签的语法解析: html同名标签转换为html同名元素, 其它标签需要特别解析
* 遇到以 { 开头的代码，以JS语法解析: 标签中的js表达式必须用{ }包含

7.babel.js的作用

浏览器不能直接解析JSX代码, 需要babel转译为纯JS的代码才能运行
只要用了JSX，都要加上type="text/babel", 声明需要babel来处理

<a id="%E5%87%BD%E6%95%B0%E5%BC%8F%E3%80%81%E7%B1%BB%E5%BC%8F-%E7%BB%84%E4%BB%B6"></a>
###### 函数式、类式 组件
* **组件名必须首字母大写**
* **虚拟DOM元素只能有一个根元素**
* **虚拟DOM元素只能有一个根元素**

<a id="state-%E5%B1%9E%E6%80%A7"></a>
###### state 属性
>1.state是组件对象最重要的属性, 值是对象(可以包含多个key-value的组合)
>
>2.组件被称为"状态机", 通过更新组件的state来更新对应的页面显示(重新渲染组件)

1. 组件中render方法中的this为组件实例对象
2. 组件自定义的方法中this为undefined，如何解决？
*. 强制绑定this: 通过函数对象的bind()
*. 箭头函数  **箭头函数，没有自己的 this，当在箭头函数中使用 this 时其 this 指向外部**

3. 状态态数据，不能直接修改或更新