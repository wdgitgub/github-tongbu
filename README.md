# github-用SSH同步方法

黑马程序员github教学视频
用ssh上传项目到github：
https://www.bilibili.com/video/av65233630?p=49&spm_id_from=pageDriver


git bash 基本命令

在本地电脑的文件夹里初始化一个git的本地仓库（本地也要成立一个git本地暂存区仓库）
git init

(查看本地git暂存区文件包里文件的状态：是否属于暂存区还是没列入暂存区，还是原来的文件包里的文件)
(git status -s)

把文件包里的所有文件都添加到本地git暂存区中
git add .

将暂存区的文件提交到本地仓库并添加提交说明
git commit -m "随便写一个版本的名字"


把本地仓库和网络上仓库绑定

git remote add origin 加上网上仓库的地址https地址或者ssh地址（github网站有写）

例如
git remote add origin git@github.com:wdgitgub/6logseq.git

第一次大上传
git push -u origion master

第二次或者以后可以直接上传
git push


自己录的视频
https://youtu.be/qf1mltQzpqo

如果git push以后
出现问题
出现
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
就说明
ssh的证书 GitHub网站上和 本地对不上

本地的证书地址默认生成是在
C:\Users\用户名称\.ssh







