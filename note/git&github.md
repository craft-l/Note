git 与Linux命令兼容

### 常用命令：

pwd          显示工作目录

ll        相当于ls -l   除文件名称外，亦将文件型态、权限、拥有者、文件大小等资讯详细列出

ls -lA     显示所有文件包括隐藏文件

cd         进入目录

mkdir			新建目录





### 查看当前项目状态

git status 

### 本地库初始化

git init

git add *

### 签名（用于区分不同开放人员，与远程库的账号密码没有关系）

* 项目级别/仓库级别：仅在当前本地库范围有效（./git/.config文件中）

  ​	git config user.name username

  ​	git config user.email yours@email.com

* 系统用户级别：登陆当前操作系统的用户范围，系统用户级别低于项目级别(~/.gitconfig)

  ​	git config --global user.name username

  ​	git config --global user.email yours@email.com

### 消息

git commit -m "更新消息" filename

### 版本前进回退

* 查看日志    git log  

* 查看历史版本    git reflog ( git log --online           git log --pre=oneline) 每次提交只显示一行
  * HEAD相当于指针，指向当前版本的仓库

* 到指定版本： gti reset --hard 哈希表索引

  ​	（补充：

  ​						hard是移动本地库指针

  ​						除了--hard以外，还有--soft 和--mixed等 ，有需要可以看help文档

  ​						使用^只可以回退：git reset --hard HEAD^(^的数量表示后退版本数)

  ​						git reset --hard HEAD~n(n表示回退次数)

​				）

### 比较文件差异

不带文件名为比较多个文件

* 将工作区文件和本地库历史记录比较      git diff 文件名        

* 将工作区文件和历史版本历史记录进行比较           git diff（HEAD指向的历史版本） 文件名          

### 分支

* 查看分支状态        git status 

* 查看已有分支       git branch -v

* 创建分支              git branch 分支名 

* 分支切换 			git checkout 分支名

* 删除分支（需切换到其他分支后再进行删除操作）              git branch -d 分支名

* 分支改名

  * 如果对于分支不是当前分支，可以使用下面代码：

    ​    git branch -m 原名 新

  * 如果是当前，那么可以使用加上新名字

    ​        git branch -m 原名 

* 合并分支			
  * 首先切换到接受修改的分支上
  * git merge 指定另一分支名字
  * 当两个分支在合并前有相同文件都分别有更新的时候，会产生冲突，需要做出人工做出处理
  * 有冲突时也可以强制合并(强制合并部分冲突数据将被舍弃)：git merge main --allow-unrelated-histories



### git与github的关联

* 使用http关联
  * 在提交或拉取文件的时候要指定地址，我们用remote命令来创建一个简短的名字来代替地址
  * 查看已经创建的别名     git remote -v
* 添加远程仓库别名
  * git remote add [shortname] [url]
* 查看远程仓库状态
  * 全部： git remote -v
  * 特指： git remote show [remote]
* 推送
  * git push 别名 分支名            如： git push origin master
* 拉取代码
  * git pull 别名 分支名
* 克隆
  * git clone 项目地址
* ssh免密登陆













