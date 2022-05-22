# git init & git add & git commit

### git就是一个命令而已
### bash命令行里有很多命令

### git解决的问题
* 一个只有程序员才有的问题:版本控制

### git可以让你的代码有版本
### 你可以随时退回到某个版本
### 当然git还有其他的强大功能

* code . 打开当前目录

### git init 初始化
  * 注意git init不要在桌面运行
  * ls 不会显示以.为开头的目录
  * ls -a 显示 a就是all
  * git init会创建.git目录
  * .git目录用来容纳你的代码快照

### git status 显示工作目录和暂存区的状态 可以看到哪些修改被暂存到了哪些没有

* git add 路径
* 选择那些变动是可以提交的
* 路径可以是绝对路径,相对路径和.和*

* .gitignore(用 法在vscode 当前目录中新建文件为.gitignore 然后把不需要提交变动的文件名输入,保存,文件名显示灰色则成功)
* 描述哪些变动是不需要提交的 
常见的有 node_modules  .DS_Store  .idea   .vscode

* git commit -m 字符串
提交,并说明理由
* 字符串里如果有空格,就要用引号包起来
例如 git commit -m "版本 1"

* git commit -v (v全称verbose 意思为啰嗦)
打开了vscode,等你输入一条信息
里面加号+的是新增的-减号是删除的
优点 能帮我们回顾刚刚改了什么东西
而且会迫使我把提交理由写得更详细一些
适合新人学习 

* git log 查看复制了多少份

### 多提交几次
* git add
* git commit -v
* 每次重复这两个操作即可
* 不要少写 不要少写空格

### git reset --hard xxxx
* xxxxx是提交号的前六位
* 请一定确保你已经把所有代码commit了
* 因为这个操作会使没有commit过的变动消失

### 版本查看方法:
1. git log
2. commit后的字符前六位
3. 输入哪个版本就会回到哪个版本

### 再次输入git log 会看不到之前的版本
* 解决方法: git reflog( 不止看当前的历史,还要看包括你御剑飞行的历史,就是你跳过来跳过去的历史,跳到不同版本的历史)
* 在git reflog 中看到之前版本,在复制前面六位后,可以跳回到任意版本

### 常见问题
* git文件存放在.git目录里

* add 和commit关系
* add是要提交的
* commit才是真正提交

* git reset --hard 
* 注意文件要不就是处于红色还未提交
* 要不就是git commit提交之后
* 不能在git add这种要提交没提交的状态
否则会被删除

## 总结
* git可以实现多版本的切换
* git add 选择要提交的内容
* .gitignore文件描述不提交的内容(在VScode中创建,里面输入不需要提交的文件名即可,不需要提交的文件会变成灰色)
* git commit -v 用来提交
* git log 用来查看历史
* git reset --hard xxxxxx(前六位数版本号)用来切换不同版本
* git reflog用来查看所有历史



### 如何同时两条线同时开发
* git branch x
* git checkout x
* git branch
基于当前commit创建的一个新的时间线(分支)
我在哪个分支提交,代码就出现在哪个分支

* git checkout
用于切换另一个分支
当前目录有未提交的代码,只要跟另一个分支不冲突,就不需理会
如果冲突了呢? 可以使用通灵术git stash ,也可以合并冲突

* git branch
用于查看分支,哪个分支有*号就在哪个分支

* 两个分支合并
git merge加分支
解决完冲突提交  commit后不加参数

* 要学会解决冲突
在合并分支的时候,会得到conflict提示
使用git status -sb 查看哪个/哪些文件冲突了
### 解决冲突
1. 依次打开每个文件
2. 搜索====四个等于号
3. 在上下两个部分中选择要保留的代码
4. 可以只选上面,也可以只选下面,甚至可以都选
删除不用的代码,删除====   >>>>   <<<<  这些标记
5. git add 对应版本
6. 再次 git  status -sb ,解决下一个文件的冲突
7. 直到没有冲突,运行git commit (注意不需要选项)
分支可以合并
8. 进入要保留的分支
9. 运行 git merge x
10. 合并完后删除无用的分支 git branch -d x

### 合并时冲突怎么办
* 解决冲突即可
* 然后git commit,默认使用的commit message
