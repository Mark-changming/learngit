# Git 学习笔记

## 	1. Git是什么？

​			Git是目前世界上最先进的分布式版本控制系统

	## 安装git

​			官网下载安装，完成输入	

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

用来自报家门

## 2. 创建版本库

```
$ mkdir learngit // 创建learngit文件夹
$ cd learngit //定位到该文件夹
$ pwd //查看当前路径
/Users/Markqaq/learngit
```

将目录初始化成git仓库

```
$ git init
Initialized empty Git repository in /Users/Markqaq/learngit/.git/
```



## 3. 添加文件到Git仓库

编写一个readme.txt文件

```
$ vim filename.txt
```

:wq保存，然后把文件添加到git仓库暂存区（stage）

```
$ git add filename.txt
```

把文件提交到分支

```
$ git commit -m "my first git file readme"
[master (root-commit) eaadf4e] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```

git 可以add多次不同的文件，commit可以一次提交很多文件



## 4. 查看仓库状态

git status命令可以随时掌握工作区/仓库当前的状态 （显示有变更的文件），有以下几种结果：

    1. Changes not staged for commit：文件更改了，但是还未进入暂存区 ，需要add；
      2. Changes to be committed：文件已进入暂存区，但还未提交到版本库，需要commit；
        3. Untracked files：表示该文件还从来没有被添加进版本库，这是新添加的文件；



## 5. 查看修改内容

如果`git status`告诉你有文件被修改过，用`git diff`可以查看修改内容，语法为：`git diff <fileName>`



## 6. 版本回退

1. git log 可以查看提交历史记录，显示从最近到最远的提交日志；git log --pretty=oneline 使每个日志单独成行。

  2. git中，用HEAD表示当前版本（commit id 版本号）。

  3. 回退到上一个版本：git reset --hard HEAD^，HEAD^表示回退1个版本，HEAD^^表示回退2个版本，HEAD~100表示回退100个版本。HEAD其实是个指向当前版本的指针。

  4. 返回过去/未来的版本：git reset --hard 新版本的commit id（前4位就行）。
  5. git reflog查看历史每一次命令，可以查看每一次提交时的commit id。


## 7. 撤销修改

未添加到暂存区， 想丢弃工作区的修改时， git checkout -- <file>

1. 若文件自修改后还没有被放到暂存区，现在，撤销修改就回到和**版本库**一模一样的状态；
2. 若文件已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到**暂存区**后的状态。



已添加到暂存区， 想丢弃修改时，第一步用命令`git reset HEAD <file>`，把暂存区的修改撤销掉（unstage），重新放回工作区 ，第二部再checkout -- <file>



## 8. 删除文件

手动删除或`rm <fileName>`删除文件，执行`git add/rm <fileName>`和`git commit-m <message>`， 删错了使用git checkout --file恢复最新版本



## 9. 重命名文件

```
$ hit mv file newfile
```



## 10. 移动文件

```
$ git mv file directory/file
```





## 11. 远程仓库

1. 创建SSH Key。

   ```
   $ ssh-keygen -t rsa -c "youremail@gmail.com"
   ```

   `id_rsa`是私钥，id_rsa.pub`是公钥

2. 打开github, 在setting里找到SSH keys, 创建New SSH key, 填上title和id_rsa.pub的内容即可

## 12. 添加远程库

使用以下命令：

``` 
$ git remote add origin git@github.com:yourgithubname/learngit.git
$ git push -u origin master  #第一次推送
$ git push origin master  #推送本地最新修改
```

## 13. 从远程库克隆

``` 
$ git clone git@github.com:yourgithubname/learngit.git
```



## 14. 创建+切换分支

```
$ git checkout -b dev
Switched to a new branch 'dev'
```



## 15. 查看当前分支

```
$ git branch
* dev
  master
```



## 16. 合并分支

```
$ git merge dev <name>
```



## 17. 删除分支

```
$ git branch -d dev
```



## 18. 切换分支

```
$ git switch -c dev
```



## 19. 解决分支合并冲突

当Git无法自动合并分支时，就必须首先解决冲突。解决冲突后，再提交，合并完成。

解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。



## 20. 标签管理

### 20.1 打上标签

``` 
$ git tag <name> <commit id>
```

### 20.2 查看标签

```
$ git show <tagname>
```

### 20.3 删除标签

```
$ git tag -d <name>
```

### 20.4 推送标签

```
$ git push origin --tags
```

