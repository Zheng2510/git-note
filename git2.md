# github 远程仓库

* rm -rf/ 全盘删除
* id_rsa 私钥(永远不要给别人看你的私钥内容)
* id_rsa.pub公钥

### 推理
* 你在github上有一个账号
* 你的git仓库在你的电脑上
* github怎么知道这个电脑和这个账号都属于你你

### 答案
* 每次输入一次密码(https协议),太不方便
* 使用ssh key
* 电脑上放私钥,github账号留下公钥
* 上传代码是用私钥加密,github用公钥解密
* 如果解开了,说明是配对的
* 同理,你怎么知道对方是github的呢?也需要github提供一个公钥给你,所以第一次链接github的时候要选择yes来接受对方的公钥,这个知识点不重要

### 将本地仓库上传到github

1. 上传代码
2. 新建github repo(github仓库,复制其ssh(注意不是http)地址
3. 复制页面里面的代码(关掉翻译)

4. git remote add origin git@xxxxxx
在本地添加远程仓库地址
origin是远程仓库的默认名字,可以换,建议不换
不要使用http://地址,因为每次都需要密码

5. git push -u origin master
推送本地master分支到远程origin的master分支
如果 提示你应该git pull ... ,你就 git pull 一下
git pull 是先把远程分支合并到本地对应的分支
如果远程分支没有更新过,才可以省略
6. git pull-u origin master 的意思是设置上游分支
之后就不用再设置上游分支了,直接git pull;git push;


### 的http和ssh一定要选ssh(因为http每一次都要输入很麻烦)

### 如何上传其他分支
* 方法一git push origin x:x  (第一个x是源头也就是本地第二个x是源头)
* 方法二
git checkout x(直接切换到x分支)
git push -u origin x

### github用来备份.git/而已

### 所有代码都可用ssh和https协议下载,知识ssh协议传输速率更高

### git clone 克隆代码
下载别人代码
* git clone git@xxxx(目标路径)
* 如果是不同机器,要写上传新的ssh key (一机一key)
1. cd 目标路径(进入目标路径)
2. git add / git commit / (git pull)/ git push 四连操作

### 如何下载某个分支
*  先下载整个仓库,然后 git checkout 分支名
或者自己去搜一些难记的命令,
### 下载速度很慢怎么办
* 看 git clone 满速下载教程

### git clone三种变形
1. git clone git@?/xxx.git  xxx指的是文件名
会在当前目录下创建一个xxx目录
xxx/.git是本地仓库
一般你需要接一句 cd xxx (要形成条件反射,创建本地仓库紧接着就要进入)

2. git clone git@?/xxx.git  yyy
会在本地新建yyy目录,记得cd yyy

3. git clone git@?/xxx.git . (注意.)
不会新建目录,使用当前目录容纳代码和.git
### 当前目录一开始最好是个空目录,不然后果自负

### 可以上传到两个远程仓库吗
* 只需要两句话
1. git remote add repo2 git@xxxx
2. git push -u repo2 master

### 如果提示git pull ...
* 说明你新建项目的时候创建了一些文件
* 你只需要运行git pull 之后在运行刚才打的命令

### 国内github的代替品
* coding.net(腾讯战略投资)
* gitlab.com
* 码云 gitee.com(开源中国)
### 建议用github,因为大牛多
### 总结
### 常用命令
* 大部分时候,你只需要git clone / git pull / git push /三个命令
* 遇到报错,请仔细看报错,翻译一下,就能猜到原因

### 远程仓库
* 只是本地仓库的备份,所以变化都要先commit 到本地仓库,然后push到远程
无法下载部分代码,只能clone整个仓库

### 老手才会的命令
* 使用bash alias简化命令
```javascript
touch ~/.bashrc
echo 'alias ga="git add"'>> ~/.bashrc
echo 'alias gc="git commit -v"'>> ~/.bashrc
echo 'alias gl="git pull"'>> ~/.bashrc
echo 'alias gp="git push"'>> ~/.bashrc
echo 'alias gco="git checkout"'>> ~/.bashrc
echo 'alias gst="git status -sb"'>> ~/.bashr
```

* 然后重启命令行,或者运行 source ~/.bashrc
就可以使用这些缩写了
bashrc(命令行配置文件)

* git rebase -i xxx 美化历史命令
r 采用 但是改写message
s采用 但是合并到上一个提交

### 出错怎么办
* 看log提示
* 仔细阅读git给出的log,里面说了怎么解决

### 中止
* git rebase --abort 可以取消rebase
继续
* git rebase --continue 可以继续
### 通灵术
* 前提要git add 待提交
* git stash(放进私藏空间)/git stash pop(从空间弹出来)
* 有时候代码不想提交,又不想删除可以找个空间私藏