>在提交代码中使用了git相关命令及配置，没系统接触过，记录如下

##### 添加git全局范围的用户名和邮箱
```bash
git config --global user.email wangjia@163.com
git config --global user.name wangjia
```

##### 配置完确定下查看
```bash
# 全局
git config --global -l


# 看所有的
git config -l

```

##### 删除全局git
```bash
git config --global --unset user.name
git config --global --unset user.email
```