### git命令大总结

* git config用来配置(六行配置)
* git add 添加路径
* git status -sb 能简单看懂的状态
* git commit -v(弹出vscode来比较信息)
* git branch x 开创一个分支叫x
* git checkout x 进入这个分支x
* git merge 合并分支
* git commit 在合并分支时不需要加选项
* git branch -d x 删除一个分支
* git log 查看记录
* git reflog 查看所有记录
* git reset --hard xxxxxx 时空穿越不同版本 xxxxxx是版本号前六位

### .git目录就是本地仓库
* 他不会重复复制相同的文件(优化)
它可以支持多个分支

### 一些细节
* git add 处理的是文件变化,而不是文件,比如你删除一个文件后,依然要用git add 来添加到待提交区
* 大部分之后,知道git add . 和git commit -v即可
* 学会命令行操作,你就不再需要用gui操作了


1. 在目录x里面运行git init的效果 :会多出一个x/.git目录,里面有一些奇奇怪怪的文件
2. 本地仓库就是git init 创建的那个.git目录
3. git add index.html 会把index.html标记为将要提交到本地仓库(to be commited)
4. 在.gitignore文件里写入node_modules的效果:git就不会把node_modules标记为要提交的文件或目录了
5. git commit -m 理由有什么用:会把已经标记为要提交的文件给提交到本地仓库,并给出理由
6. git commit -v 优点:可以帮助我们回顾改了什么,可以促使我们写出更长的提交理由
7. git branch x 作用:会基于本地仓库里最新一次commit(提交),创建一个新的分支x
8. git checkout x 作用:会让当前目录的内容变成本地仓库里x分支的最新内容(可能会删除当前目录里的一些文件)
9. git reset --hard xxxxxx命令需要注意:xxxxxx是commit的号码,可以是六位四位七位只要是唯一的即可
运行reset命令前,一定要确保重要代码已经提交(commit)否则后悔莫及