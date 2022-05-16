# github-用SSH同步方法

- 黑马程序员github教学视频
- 用ssh上传项目到github：
- https://www.bilibili.com/video/av65233630?p=49&spm_id_from=pageDriver


- git bash 基本命令

# 在本地电脑的文件夹里初始化一个git的本地仓库
（本地也要成立一个git本地暂存区仓库）

```
git init
```
如果git init没有产生一个本地叫.git的本地文件包
就打开隐藏文件的显示
查看》选项》查看》显示隐藏文件和文件夹


# 添加一个readme文件

```
git add README.md
```
如果出现
hint: core.useBuiltinFSMonitor=true is deprecated;please set core.fsmonitor=true
 instead
hint: Disable this message with "git config advice.useCoreFSMonitorConfig false"
fatal: pathspec 'README.md' did not match any files


# 添加一个版本号
```
git commit -m ""
```
""里随便写一个版本号

# 添加到github网上这个仓库的 到网上的main 列表里
```
git branch -M main
```
或者
添加到github网上这个仓库的 maste 列表里
```
git branch -M master
```




# 第一种方法 用http上传文件
# 绑定网上空间和线下空间（第一种方法用http） 
```
git remote add origin 加网址
```
例如
```
git remote add origin https://github.com/wdgitgub/6logseq.git
```

问题：

如果出现
```
fatal: remote origin already exists. (远程来源已经存在)
```

我们可以先 
```
git remote -v 
```
查看远程库信息
 出现
```
origin  git@github.com:wdgitgub/6logseq.git (fetch)
origin  git@github.com:wdgitgub/6logseq.git (push)
origion git@github.com:wdgitgub/6logseq.git (fetch)
origion git@github.com:wdgitgub/6logseq.git (push)
```


可以看到，本地库已经关联了origin的远程库，并且，该远程库指向GitHub

解决办法如下：

1、先输入删除关联的命令
```
git remote rm origin
```
(删除关联的origin的远程库)

2、再输入

```
git remote add origin 加网址
```
例如

```
git remote add origin https://github.com/wdgitgub/6logseq.git
```

就不会报错了！

3、如果输入$ 
```
git remote rm origin 
```
还是报错的话，

error: Could not remove config section 'remote.origin'. 我们需要修改gitconfig文件的内容

4、找到你的github的安装路径，我的是C:\Users\ASUS\AppData\Local\GitHub\PortableGit_ca477551eeb4aea0e4ae9fcd3358bd96720bb5c8\etc

5、找到一个名为gitconfig的文件，打开它把里面的[remote "origin"]那一行删掉就好了！





# 第一次上传用这个命令
```
git push  -u origin main
```

# 第二次和以后上传用这个命令
```
git push
```

问题：

如果出现
fatal: unable to access '网址': OpenSSL SSL_read: Connection was reset,
errno 10054

一般是这是因为服务器的SSL证书没有经过第三方机构的签署，所以才报错
参考网上的解决方法：输入

```
git config --global http.sslVerify “false”
```
解除ssl验证后，再次git即可


如果出现
fatal: bad boolean config value '“false”' for 'http.sslverify'
则用这个网站上的方法
https://blog.csdn.net/wangxingxingalulu/article/details/118392299









# 第二种方法 用ssh上传


```
git remote add origin git@github.com:wdgitgub/9.git
```
```
git push -u origin main
```






(查看本地git暂存区文件包里文件的状态：是否属于暂存区还是没列入暂存区，还是原来的文件包里的文件)

```
git status -s
```

把文件包里的所有文件都添加到本地git暂存区中
```
git add .
```

将暂存区的文件提交到本地仓库并添加提交说明
```
git commit -m ""
```
"随便写一个版本的名字"

把本地仓库和网络上仓库绑定
```
git remote add origin 
```
加上网上仓库的地址https地址或者ssh地址（github网站有写）

例如
```
git remote add origin git@github.com:wdgitgub/6logseq.git
```

第一次大上传
```
git push -u origion master
```

第二次或者以后可以直接上传
```
git push
```


自己录的视频
https://youtu.be/qf1mltQzpqo

如果git push以后
出现问题
出现
```
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
```
就说明
ssh的证书 GitHub网站上和 本地对不上

本地的证书地址默认生成是在
C:\Users\用户名称\.ssh







