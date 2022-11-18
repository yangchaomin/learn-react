[TOC]
# learn-react
学习React记录
>项目中代码都来自于学习网络上视频或教程，本人前端完全不会从0开始，希望大家都能学有所成。

##### 前言 第一次提交
github 的相关操作也是从0开始学习，第一次提交也是一波三折
1. LibreSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:44 <br/>
    通过百度找到解决方案：
>问题原因 因为 Git 的Http代理的问题，Git支持三种协议： git、ssh、http
本来push的时候应该走ssh隧道的，但是因为设置了http代理，所以就走了http的代理，于是就提交不了了。<br/>
解决方案<br/>
git config --global --unset http.proxy

2. remote: Support for password authentication was removed on August 13, 2021. 密码模式被移除了
    解决方案有 使用ssh免密登录、使用personal access token，我选择了使用 使用personal access token

###### 配置 使用personal access token
登录 github，按照如下路径：<br/>
>Settings => Developer Settings => Personal Access Token => Generate New Token  => 填写表格 => Generate token => 复制PAT
**注意是在登录头像下面的 Settings 菜单中，在仓库的 Settings 中是找不到的**
复制生成Token后，因为我已经提交过一次，虽然失败了但是 git 已经记录了密码，需要把之前的记录删掉<br/>

>For macOS <br/>
Click on the Spotlight icon (magnifying glass) on the right side of the menu bar. Type Keychain access then press the Enter key to launch the app => In Keychain Access, search for github.com => Find the internet password entry for github.com => Edit or delete the entry accordingly => You are done

详细参考地址：[Message "Support for password authentication was removed. Please use a personal access token instead."](https://stackoverflow.com/questions/68775869/message-support-for-password-authentication-was-removed-please-use-a-personal)

密码就使用复制的 PAT，随后提交中也要使用 PAT 码，跌跌撞撞第一次提交终于成功了！

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