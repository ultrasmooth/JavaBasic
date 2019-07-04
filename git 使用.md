## 新建一个git仓库

1，首先在你需要进行代码版本管理的位置，右键，选择git bash here

1，输入一个命令 ： git init      这个命令的目的是初始化git管理信息，创建一个.git文件夹

2，每次你想要把代码暂存，输入命令： git add .

3，把代码提交： git commit -m '版本备注信息'

##  git 使用

```shell
 git status   // 查看是否还有文件未提交

 git diffr readme.txt 查看readme.txt文件提交了什么内统

 git log 查看文件
 
 git log --pretty=oneline   //查看精简日志
 
 git reset --hard HEAD^   //回退到上一个版本
 
 git reset --hard HEAD~100
 
```

#### 提交文件两部曲
```shell
git add
git commit -m"提交注释"
```

#### 删除一个版本,然后恢复

```java
git reflog //获取上一个版本
git reset --hard 6fcfc89  //假如版本号是6fcfc89
```

#### 理解工作区与暂存区

* 工作区:就是你在电脑上看到的目录,比如目录testgit里的文件(.git隐藏目录版本库除外).或者以后需要再更新建目录文件等等都属于工作与范畴
* 版本库(Repository): 工作区有一隐藏目录.git,这个不属于工作区,这是版本库 其中版本库里面存了很多东西,其中最重要的就是stage(暂存区),还有git为哦我们自动创建了第一个分支mater,以及指向master的指针HEAD
* 前面说过使用Git提交文件到版本库有两步

```shell
git add    //第一步,实际上就是把文件添加到暂存区
git commit //实际上就是把暂存区的所有内容提交到当前分支上
```

#### git撤销修改和删除文件操作

* 撤销修改

```shell
//使用 git checkout --file
git checkout --readme.txt
/*
有两种情况:
1.readme.txt自动修改后,还没有放到暂存区,使用撤销修改就回到和版本库一模一样的状态.
2.readme.txt已经放入暂存区了,接着又做修改,撤销修改就回到添加暂存区后的状态-
```

* 删除操作

```shell
rm test.txt
```

* 这个时候我们有两种选择:
* 第一种就是: commit
* 第二种就是: 使用 git chekout -- 文件名  把文件恢复



## 远程仓库

git 仓库和github仓库之间的传输时通过SSH加密的,所以需要一点设置

* 传送到远程仓库

```shell
git puch origin master
```



## 创建和合并分支

* 创建dev分支,然后切换到dev分支上
* git checkout -b dev    //创建并切换分支
* git branch   //查看当前分支

```shell
//git checkout -b dev相当于下面两条命令
git brach dev
git checkout dev
```





