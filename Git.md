# Git

内容摘抄自：https://blog.csdn.net/u011863024/article/details/118562748

## 1、Git工作机制

![git工作机制](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/git%E5%B7%A5%E4%BD%9C%E6%9C%BA%E5%88%B6.png)



## 2、Git安装

 官网下载安装包，切换安装路劲后默认下一步安装 。

git选项配置：![git配置](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/git%E9%85%8D%E7%BD%AE.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/git%E9%85%8D%E7%BD%AE2.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/git%E9%85%8D%E7%BD%AE3.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/git%E9%85%8D%E7%BD%AE4.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/git%E9%85%8D%E7%BD%AE5.png)

![git配置6.png](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/git%E9%85%8D%E7%BD%AE6.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/git%E9%85%8D%E7%BD%AE7.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/git%E9%85%8D%E7%BD%AE8.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/git%E9%85%8D%E7%BD%AE9.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/git%E9%85%8D%E7%BD%AE10.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/git%E9%85%8D%E7%BD%AE11.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/git%E9%85%8D%E7%BD%AE12.png)

## 3、Git常用命令

|               命令名称               |       作用        |
| :----------------------------------: | :---------------: |
| git config --global user.name 用户名 |   设置用户签名    |
| git config --global user.email 邮箱  | 设置用户email地址 |
|               git init               |   初始化本地库    |
|              git status              |  查看本地库状态   |
|            git add 文件名            |   添加到暂存区    |
|   git commit -m “日志信息” 文件名    |   提交到本地库    |
|              git reflog              |   查看历史记录    |
|       git reset --hard 版本号        |     版本穿梭      |

### 3.1设置用户签名 

```
git config --global user.name 用户名
git config --global user.email 邮箱
```

说明：**签名的作用是区分不同操作者身份**。用户的签名信息在每一个版本的提交信息中能够看到，以此确认本次提交是谁做的。 **Git 首次安装必须设置一下用户签名，否则无法提交代码**。

***注意***： 这里设置用户签名和将来登录 GitHub（或其他代码托管中心）的账号没有任何关系。



查看设置过的用户签名

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop
$ cat ~/.gitconfig
[user]
        name = abc
        email = abc@123.com
[core]
        quotepath = false
```

### 3.2初始化本地库

新建一个文件夹，使用git命令窗口进入，初始化本地库：**git init**

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git init
Initialized empty Git repository in C:/Users/abc/Desktop/HelloGit/.git/

# 创建了一个名为.git非空隐藏文件夹
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ ls -al
total 8
drwxr-xr-x 1 abc 197121 0 Jul  5 20:19 ./
drwxr-xr-x 1 abc 197121 0 Jul  5 20:19 ../
drwxr-xr-x 1 abc 197121 0 Jul  5 20:19 .git/
```

创建了一个名为.git的非空隐藏文件夹

### 3.3查看本地库状态

查看本地库状态：**git status**

#### 3.3.1首次查看（工作区没有任何文件）

```
# 首次查看（工作区没有任何文件）
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

#### 3.3.2新增文件(hello.txt)

```
# 新增文件（hello.txt）
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ vim hello.txt

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ cat hello.txt
hello, git!
hello, git!
```

#### 3.3.3再次查看确认(检测到未追踪的文件)

```
# 再次查看（检测到未追踪的文件）
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        hello.txt

nothing added to commit but untracked files present (use "git add" to track)
```

### 3.4添加暂存区

添加暂存区：**git add 文件名**

#### 3.4.1将工作区的文件提交到暂存区

```
#添加至暂存区
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git add hello.txt
warning: LF will be replaced by CRLF in hello.txt.
The file will have its original line endings in your working directory
```

#### 3.4.2查看状态(检测到暂存区有新文件)

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   hello.txt
```

#### 3.4.3移除暂存区的hello.txt

```
#移除暂存区的hello.txt
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git rm --cached hello.txt
rm 'hello.txt'

#再次查看暂存区中的文件已被删除，需要重新添加
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        hello.txt

nothing added to commit but untracked files present (use "git add" to track)

# 再次添加
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git add hello.txt
warning: LF will be replaced by CRLF in hello.txt.
The file will have its original line endings in your working directory
```

### 3.5提交本地库

提交本地库：**git commit -m "日志信息" 文件名**

#### 3.5.1将暂存区的文件提交到本地库

```
#提交本地库abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git commit -m "first commit" hello.txt[master (root-commit) b0006bc] first commit 1 file changed, 19 insertions(+) create mode 100644 hello.txt
```

#### 3.5.2查看状态(没有文件需要提交)

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git statusOn branch masternothing to commit, working tree clean
```

#### 3.5.3查看版本信息 

```
#查看版本信息命令
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git reflog
b0006bc (HEAD -> master) HEAD@{0}: commit (initial): first commit

#查看详细日志命令
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git log
commit b0006bc538b98b7eb77b4b4aaa17b6e333c4289e (HEAD -> master)
Author: abc <abc@123.com>
Date:   Tue Jul 6 00:38:24 2021 +0800

    first commit
```

### 3.6修改文件(hello.txt)

修改文件内容：**$ vim hello.txt**

#### 3.6.1查看状态(检测到工作区有文件被修改)

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ vim hello.txt

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ cat hello.txt //查看文件内容
hello, git!222
hello, git!
hello, git!
hello, git!
hello, git!

#提示 hello.txt 被修改过（modified）
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   hello.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

#### 3.6.2将修改的文件再次添加到暂存区

```
# 将修改的文件再次添加暂存区
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git add hello.txt
warning: LF will be replaced by CRLF in hello.txt.
The file will have its original line endings in your working directory

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore <file>..." to unstage)
        modified:   hello.txt
 
# 第2次提交
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git commit -m "second commit" hello.txt
[master 6967bf0] second commit
 1 file changed, 1 insertion(+)
```

#### 3.6.3查看状态(工作区的修改添加到暂存区)

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git status
On branch master
nothing to commit, working tree clean

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git reflog
6967bf0 (HEAD -> master //指针指向该版本) HEAD@{0}: commit: second commit
b0006bc HEAD@{1}: commit (initial): first commit
```

### 3.7历史本版

查看版本信息：**git reflog**

查看版本详细信息：**git log** 

**`git log`** 命令可以显示所有提交过的版本信息，如果感觉太繁琐，可以加上参数 `--pretty=oneline`，只会显示版本号和提交时的备注信息。

`git reflog` 可以查看所有分支的所有操作记录（包括已经被删除的 `commit` 记录和 `reset` 的操作）。例如，执行 `git reset --hard HEAD~1`，退回到上一个版本，用`git log`则是看不出来被删除的`commitid`，用`git reflog`则可以看到被删除的`commitid`，可以恢复到被删除的那个版本。

```
Git 切换版本， 底层其实是移动的 HEAD 指针。
```

#### 3.7.1查看历史版本

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git reflog41f776b (HEAD -> master) HEAD@{0}: commit: third commit6967bf0 HEAD@{1}: commit: second commitb0006bc HEAD@{2}: commit (initial): first commitabc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git logcommit 41f776ba69ea06c42bd449098d818ab73608d4dd (HEAD -> master)Author: abc <abc@123.com>Date:   Tue Jul 6 01:18:21 2021 +0800    third commitcommit 6967bf01bdcbc8e326f1b8c45d45db8bd4c0c868Author: abc <abc@123.com>Date:   Tue Jul 6 01:02:10 2021 +0800    second commitcommit b0006bc538b98b7eb77b4b4aaa17b6e333c4289eAuthor: abc <abc@123.com>Date:   Tue Jul 6 00:38:24 2021 +0800    first commit
```

#### 3.7.2版本穿梭

**git reset --hard 版本号**

```
# 首先查看当前的历史记录abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git reflog41f776b (HEAD -> master) HEAD@{0}: commit: third commit6967bf0 HEAD@{1}: commit: second commitb0006bc HEAD@{2}: commit (initial): first commit# 切换到 b0006bc 版本，也就是第一次提交的版本abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git reset --hard b0006bcHEAD is now at b0006bc first commit# 切换完毕之后再查看历史记录，当前成功切换到了 b0006bc 版本abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git reflogb0006bc (HEAD -> master) HEAD@{0}: reset: moving to b0006bc41f776b HEAD@{1}: commit: third commit6967bf0 HEAD@{2}: commit: second commitb0006bc (HEAD -> master) HEAD@{3}: commit (initial): first commit# 然后查看文件 hello.txt，发现文件内容回到第一版本abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ cat hello.txthello, git!hello, git!hello, git!
```

## 4、Git分支操作

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/4%E5%88%86%E6%94%AF.png)

#### 4.1什么是分支

在版本控制过程中，同时推进多个任务，为每个任务，我们就可以创建每个任务的单独分支。使用分支意味着程序员可以把自己的工作从开发主线上分离开来， 开发自己分支的时候，不会影响主线分支的运行。对于初学者而言，分支可以简单理解为副本，一个分支就是一个单独的副本。（分支底层其实也是指针的引用）

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/4%E5%88%86%E6%94%AF2.png)

#### 4.2分支的好处

同时并行推进多个功能开发，**提高开发效率**。

各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响。失败的分支删除重新开始即可。

#### 4.3分支的操作

|      命令名称       |             作用             |
| :-----------------: | :--------------------------: |
|  git branch 分支名  |           创建分支           |
|    git branch -v    |           查看分支           |
| git checkout 分支名 |           切换分支           |
|  git merge 分支名   | 把指定的分支合并到当前分支上 |

##### 4.3.1查看分支

**git branch -v**

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git branch -v
* master b0006bc first commit
```

##### 4.3.2创建分支

**git branch 分支名**

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git branch hot-fix //创建一个新得分支(自命名)

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git branch -v
  hot-fix b0006bc first commit //刚创建的新的分支，并将主分支master的内容复制了一份
* master  b0006bc first commit
```

##### 4.3.3切换分支

**git checkout 分支名**

```
abc@DESKTOP-R8 5C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git checkout hot-fix //切换到新分支hot-fix
Switched to branch 'hot-fix'

# 切换到刚创建的分支上
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)
$ git branch -v
* hot-fix b0006bc first commit //*号在此，当前在该分支
  master  b0006bc first commit
```

##### 4.3.4修改分支

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)
$ vim hello.txt

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)
$ cat hello.txt
hello, git!hot-fix
hello, git!
hello, git!

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)
$ git status
On branch hot-fix
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   hello.txt

no changes added to commit (use "git add" and/or "git commit -a")

#添加到缓存区
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)
$ git add hello.txt 

#在hot-fix分支修改后的文件
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)
$ git commit -m "hot-fix first commit"
[hot-fix 25f62d6] hot-fix first commit
 1 file changed, 1 insertion(+), 1 deletion(-)

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)   
$ git reflog
25f62d6 (HEAD -> hot-fix) HEAD@{0}: commit: hot-fix first commit
b0006bc (master) HEAD@{1}: checkout: moving from master to hot-fix
b0006bc (master) HEAD@{2}: reset: moving to b0006bc
5f8dbf6 HEAD@{3}: commit: forth commit
b0006bc (master) HEAD@{4}: reset: moving to b0006bc
41f776b HEAD@{5}: commit: third commit
6967bf0 HEAD@{6}: commit: second commit
b0006bc (master) HEAD@{7}: commit (initial): first commit
```

##### 4.3.5合并分支

**git merge 分支名**

在 master 分支上合并 hot-fix 分支（将hot-fix的合并到master）

```
# 首先要切换到master分支上abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)$ git checkout masterSwitched to branch 'master'#将hot-fix的合并到masterabc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git merge hot-fixUpdating b0006bc..25f62d6Fast-forward  hello.txt | 2 +- 1 file changed, 1 insertion(+), 1 deletion(-)#合并后，可以在master分支上看到hot-fix上分支对文件的修改abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ cat hello.txthello, git!hot-fixhello, git!hello, git!hello, git!#合并后，hot-fix分支依然存在，并未消失abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git branch -v  hot-fix 25f62d6 hot-fix first commit* master  25f62d6 hot-fix first commitabc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git branch hot-fix //创建分支命令fatal: A branch named 'hot-fix' already exists.abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git checkout hot-fixSwitched to branch 'hot-fix'abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)
```

##### 4.3.6产生冲突

原因：合并分支时，两个分支**在同一个文件的同一个位置有两套完全不同的修改**。 Git 无法替我们决定使用哪一个，因此，必须**人为决定**新代码内容。

1.首先，在master修改文件hello.txt最后一行内容，并提交：

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ vim hello.txtabc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ cat hello.txthello, git!hot-fixhello, git!hello, git!hello, git!master testabc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git statusOn branch masterChanges not staged for commit:  (use "git add <file>..." to update what will be committed)  (use "git restore <file>..." to discard changes in working directory)        modified:   hello.txtno changes added to commit (use "git add" and/or "git commit -a")abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git add hello.txtabc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git commit -m "master test"[master fb0e30b] master test 1 file changed, 2 insertions(+), 2 deletions(-)
```

2.然后，在hot-fix修改文件hello.txt最后一行内容，并提交：

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git checkout hot-fixSwitched to branch 'hot-fix'abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)$ vim hello.txtabc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)$ cat hello.txthello, git!hot-fixhello, git!hello, git!hello, git!hot-fix testabc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)$ git add hello.txtabc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)$ git commit -m "hot-fix test"[hot-fix 47d2d8f] hot-fix test 1 file changed, 1 insertion(+), 1 deletion(-)
```

3.切换到master分支，然后将hot-fix分支的合并到master，冲突产生：

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (hot-fix)
$ git checkout master
Switched to branch 'master'

# 冲突产生
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git merge hot-fix //将hot-fix合并到master分支
Auto-merging hello.txt
CONFLICT (content): Merge conflict in hello.txt
Automatic merge failed; fix conflicts and then commit the result.

# MERGING 出现，表示有冲突待解决
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master|MERGING)
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   hello.txt

no changes added to commit (use "git add" and/or "git commit -a")

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master|MERGING)
$ cat hello.txt
hello, git!hot-fix
hello, git!
<<<<<<< HEAD
hello, git!hot-fix test
hello, git!master test
=======
hello, git!
hello, git!hot-fix test
>>>>>>> hot-fix
```

##### 4.3.7解决冲突

编辑有冲突的文件，**删除特殊符号**，决定要使用的内容

```
<<<<<<< HEAD
当前分支的代码 
======= 
合并过来的代码 
>>>>>>> hot-fix


abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master|MERGING)
$ cat hello.txt
hello, git!hot-fix
hello, git!
<<<<<<< HEAD
hello, git!hot-fix test
hello, git!master test
=======
hello, git!
hello, git!hot-fix test
>>>>>>> hot-fix

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master|MERGING)
$ vim hello.txt

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master|MERGING)
$ cat hello.txt
hello, git!hot-fix
hello, git!
hello, git!hot-fix test
hello, git!master test

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master|MERGING)
$ git status
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   hello.txt

no changes added to commit (use "git add" and/or "git commit -a")

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master|MERGING)
$ git add hello.txt

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master|MERGING)
$ git commit -m "conflict solved" (文件名【省略】) //提交文件时不能用文件名，否则会报错(不知道是那个文件)
[master 785ab46] conflict solved

# (master|MERGING)的|MERGING消失了，代表冲突解决了
```

#### 4.4创建分支和切换分支图解

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/4%E5%88%9B%E5%BB%BA%E5%88%86%E6%94%AF3.png)

`master`、 `hot-fix` 其实都是指向具体版本记录的指针。当前所在的分支，其实是由 `HEAD`决定的。所以创建分支的本质就是多创建一个指针。

`HEAD` 如果指向 `master`，那么我们现在就在 `master` 分支上。
`HEAD` 如果执行 `hot-fix`，那么我们现在就在 `hot-fix` 分支上。
所以切换分支的本质就是移动 `HEAD` 指针。

## 5、Git团队协作机制

### 5.1团队协作

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/5git%E5%8D%8F%E4%BD%9C.png)

###  5.2跨团队协作

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/5git%E8%B7%A8%E5%9B%A2%E5%8D%8F%E4%BD%9C.png)

## 6、GitHub操作

[Github网址](https://github.com/)

### 6.1创建远程仓库

- 登录GitHub后，点击网页右上角+号-->New repository，创建远程库。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E5%88%9B%E5%BB%BA%E8%BF%9C%E7%A8%8B%E5%BA%93.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E5%88%9B%E5%BB%BA%E8%BF%9C%E7%A8%8B%E5%BA%931.png)

### 6.2远程仓库操作

|              命令名称              |                           作用                            |
| :--------------------------------: | :-------------------------------------------------------: |
|           git remote -v            |                 查看当前所有远程地址别名                  |
|    git remote add 别名 远程地址    |                          起别名                           |
|         git push 别名 分支         |              推送本地分支上的内容到远程仓库               |
|         git clone 远程地址         |                将远程仓库的内容克隆到本地                 |
| git pull 远程库地址别名 远程分支名 | 将远程仓库对于分支最新内容拉下来后与 当前本地分支直接合并 |

#### 6.2.1创建远程仓库别名

`git remote -v` 查看当前所有远程地址别名

`git remote add 别名 远程地址`

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git remote -v

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git remote add hellogit(建议于本地仓库名一致) https://github.com/abc/HelloGit.git(GitHub上复制)

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git remote -v
//既可以推送也可拉取，所以生成了两
hellogit        https://github.com/abc/HelloGit.git (fetch) 
//既可以推送也可拉取，所以生成了两
hellogit        https://github.com/abc/HelloGit.git (push) 
```

```
GitHub仓库地址：https://github.com/Moe-Q/myfirst.git
```

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E5%88%9B%E5%BB%BA%E8%BF%9C%E7%A8%8B%E5%BA%933.png)

#### 6.2.2推送本地分支到远程仓库

`git push 别名 分支`

```
# 将master分支推送到别名为hellogit远程地址，# 也就推送到https://github.com/abc/HelloGit.git# 这里需要授权认证操作（输入账号密码），有可能推送失败，需要多次尝试！abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git push hellogit masterfatal: unable to access 'https://github.com/abc/HelloGit.git/': OpenSSL SSL_read: Connection was reset, errno 10054abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)$ git push hellogit masterEnumerating objects: 13, done.Counting objects: 100% (13/13), done.Delta compression using up to 8 threadsCompressing objects: 100% (9/9), done.Writing objects: 100% (13/13), 1.02 KiB | 523.00 KiB/s, done.Total 13 (delta 4), reused 0 (delta 0), pack-reused 0remote: Resolving deltas: 100% (4/4), done.To https://github.com/abc/HelloGit.git * [new branch]      master -> master
```

推送成功后，刷新仓库，本地代码出现在仓库中

#### 6.2.3拉取远程仓库到本地

`git pull 别名 分支`

在Github上修改hello.txt文件，并提交，然后将远程仓库代码拉取到本地。

远程仓库拉取到本地会自动进行提交。

```
#从hellogit拉取到master分支上
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git pull hellogit master
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 672 bytes | 168.00 KiB/s, done.
From https://github.com/JallenKwong/HelloGit
 * branch            master     -> FETCH_HEAD
   785ab46..47e257f  master     -> hellogit/master
Updating 785ab46..47e257f
Fast-forward
 hello.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

# 可看到从Github上修改后痕迹
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ cat hello.txt
hello, git!hot-fix
hello, git!
hello, git!modify from Github editor
hello, git!hot-fix test
hello, git!master test

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git status
On branch master
nothing to commit, working tree clean

abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit (master)
$ git reflog
47e257f (HEAD -> master, hellogit/master) HEAD@{0}: pull hellogit master: Fast-forward
785ab46 HEAD@{1}: commit (merge): conflict solved
fb0e30b HEAD@{2}: checkout: moving from hot-fix to master
```

#### 6.2.4克隆远程仓库到本地

`git clone 远程地址`

在远程库获取地址URL

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E5%85%8B%E9%9A%86%E8%BF%9C%E7%A8%8B%E5%BA%934.png)

创建一个新文件夹，将远程库代码克隆到本地新文件中。

**克隆公共库时不需要登录账号**

```
# 创建一个新文件夹abc@DESKTOP-R85C9HV MINGW64 ~/Desktop$ mkdir HelloGit-cloneabc@DESKTOP-R85C9HV MINGW64 ~/Desktop$ cd HelloGit-clone/# 在新的文件夹内，克隆远程库到本地abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit-clone$ git clone https://github.com/abc/HelloGit.gitCloning into 'HelloGit'...remote: Enumerating objects: 16, done.remote: Counting objects: 100% (16/16), done.remote: Compressing objects: 100% (7/7), done.remote: Total 16 (delta 5), reused 12 (delta 4), pack-reused 0Receiving objects: 100% (16/16), done.Resolving deltas: 100% (5/5), done.abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit-clone$ git remote -vfatal: not a git repository (or any of the parent directories): .gitabc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit-clone$ lsHelloGit/abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit-clone$ cd HelloGit/abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit-clone/HelloGit (master)$ git remote -v//自动创建了别名originorigin  https://github.com/abc/HelloGit.git (fetch)//自动创建了别名originorigin  https://github.com/abc/HelloGit.git (push)abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit-clone/HelloGit (master)$ git reflog47e257f (HEAD -> master, origin/master, origin/HEAD) HEAD@{0}: clone: from https://github.com/JallenKwong/HelloGit.git
```

**clone 会自动做如下操作：**

1. **拉取代码。**
2. **初始化本地仓库。**
3. **创建别名。**

#### 6.2.5邀请加入团队

1.选择邀请合作者

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E9%82%80%E8%AF%B7%E5%9B%A2%E9%98%9F5.png)

2. 填入目标合作者。![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E9%82%80%E8%AF%B7%E5%9B%A2%E9%98%9F6.png)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                

3.复制网址发送给你目标合作者 ， 复制红框中的内容发送。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E9%82%80%E8%AF%B7%E5%9B%A2%E9%98%9F7.png)

4.目标合作者接收到网址，用浏览器打开它，点击接受邀请。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E9%82%80%E8%AF%B7%E5%9B%A2%E9%98%9F8.png)

5.接受邀请成功之后，可以在目标合作者Github账号上看到将来共同开发远程仓库。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E9%82%80%E8%AF%B7%E5%9B%A2%E9%98%9F9.png)

6.目标合作者可以修改内容并 push 到远程仓库。

```
# 编辑 clone 下来的文件
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/pro-linghuchong/git-shTest(master)
$ vim hello.txt
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/pro-linghuchong/git-shTest(master)
$ cat hello.txt
hello git! hello atguigu! 2222222222222
hello git! hello atguigu! master test
hello git! hello atguigu! hot-fix test

# 将编辑好的文件添加到暂存区
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/pro-linghuchong/git-shTest(master)
$ git add hello.txt

# 将暂存区的文件上传到本地库
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/pro-linghuchong/git-shTest(master)
$ git commit -m "lhc commit" hello.txt
[master 5dabe6b] lhc commit
1 file changed, 1 insertion(+), 1 deletion(-)

# 将本地库的内容 push 到远程仓库
Layne@LAPTOP-Layne MINGW64 /d/Git-Space/pro-linghuchong/git-shTest
(master)
$ git push origin master
Logon failed, use ctrl+c to cancel basic credential prompt.
Username for 'https://github.com': atguigulinghuchong
Counting objects: 3, done.
Delta compression using up to 12 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 309 bytes | 309.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/atguiguyueyue/git-shTest.git
7cb4d02..5dabe6b master -> master
```

7.回到发送合作邀请者的 GitHub 远程仓库中可以看到，最后一次是目标合作者提交的。

![img](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E9%82%80%E8%AF%B7%E5%9B%A2%E9%98%9F10.png)

![img](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E9%82%80%E8%AF%B7%E5%9B%A2%E9%98%9F11.png)

### 6.3跨团队协作

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/5git%E8%B7%A8%E5%9B%A2%E5%8D%8F%E4%BD%9C.png)

1.将远程仓库的地址复制发给邀请跨团队协作的人，比如东方不败。

2.在东方不败的 GitHub 账号里的地址栏复制收到的链接，然后点击 网页右上方的Fork按钮，将项目叉到自己的本地仓库。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E8%B7%A8%E5%9B%A2%E5%8D%8F%E4%BD%9C1.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E8%B7%A8%E5%9B%A2%E5%8D%8F%E4%BD%9C2.png)

叉成功后可以看到当前仓库信息。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E8%B7%A8%E5%9B%A2%E5%8D%8F%E4%BD%9C3.png)

3.东方不败就可以在线编辑叉取过来的文件。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E8%B7%A8%E5%9B%A2%E5%8D%8F%E4%BD%9C4.png)

4.编辑完毕后，填写描述信息并点击左下角绿色按钮提交。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E8%B7%A8%E5%9B%A2%E5%8D%8F%E4%BD%9C5.png)

5.接下来点击上方的 Pull 请求，并创建一个新的请求。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E8%B7%A8%E5%9B%A2%E5%8D%8F%E4%BD%9C6.png)

6.回到岳岳 GitHub 账号可以看到有一个 Pull request 请求。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E8%B7%A8%E5%9B%A2%E5%8D%8F%E4%BD%9C7.png)

进入到聊天室，可以讨论代码相关内容。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E8%B7%A8%E5%9B%A2%E5%8D%8F%E4%BD%9C8.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E8%B7%A8%E5%9B%A2%E5%8D%8F%E4%BD%9C9.png)

7.如果代码没有问题，可以点击 Merge pull reque 合并代码。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHub%E8%B7%A8%E5%9B%A2%E5%8D%8F%E4%BD%9C10.png)

### 6.4SSH免密登录

1.可以看到远程仓库中还有一个 SSH 的地址，因此我们也可以使用 SSH 进行访问。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHubSSH%E7%99%BB%E5%BD%951.png)

2.先到C盘用户的主页目录，删除.ssh文件夹（如果没有.ssh文件夹，忽略此步）：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHubSSH%E7%99%BB%E5%BD%952.png)

```
//删除本地ssh文件夹
abc@DESKTOP-R85C9HV MINGW64 ~
$ cd ~

abc@DESKTOP-R85C9HV MINGW64 ~
$ pwd
/c/Users/abc

abc@DESKTOP-R85C9HV MINGW64 ~
$ ls -a .ssh
./  ../  id_rsa  id_rsa.pub

abc@DESKTOP-R85C9HV MINGW64 ~
$ rm -rf .ssh

abc@DESKTOP-R85C9HV MINGW64 ~
$ ls -a .ssh
ls: cannot access '.ssh': No such file or directory
```

3.运行命令`ssh-keygen`生成`.ssh`目录：

`$ ssh-keygen -t rsa -C myfirst`

**$ ssh-keygen**(生成、管理和转换认证密钥)

 **-t**(指定要创建的密钥类型) 

**rsa**(非对称加密协议) 

**-C**(大写/提供一个新注释) 

**myfirst**(注释)

```
abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit-clone/HelloGit (master)
$ ssh-keygen -t rsa -C abc@123.com
//输入后前三次回车键
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/abc/.ssh/id_rsa):
Created directory '/c/Users/abc/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/abc/.ssh/id_rsa
Your public key has been saved in /c/Users/abc/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:aeNMB/hP2yiH/Dka2jK9BJciSgA8yKKLlKXX8oei7J0 jallenkwong@163.com
The key's randomart image is:
+---[RSA 3072]----+
|=                |
|++ .   .         |
|+ = . . .        |
|.= o . . +       |
|o.o + + S o      |
|o. o + @ * +     |
|. o . ..O = .    |
| o. . o+.=..     |
|.. E  .o+oo.     |
+----[SHA256]-----+
```

4.运行完成后在本地生成ssh文件夹，把公钥里的内容全部复制到GitHub对应位置。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHubSSH%E7%99%BB%E5%BD%953.png)

```
abc@DESKTOP-R85C9HV MINGW64 ~$ ls -a .ssh./  ../  id_rsa  id_rsa.pub# 生成公钥abc@DESKTOP-R85C9HV MINGW64 ~$ cat .ssh/id_rsa.pubssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQChXy8I20br9nu4GCNeZSDkozfHvlRFpXiImYnVlHVvyvFgjct1/zMeJgot1J6+yArSJbA4TMlS9nG8owCE6C9yqhPceDlKtQbARKS2pW7IyP5OhIbcqVmWmvvd+IMmsWrWgK9S6jqp0xSqv3Z3mlcHWOAK18oOe6wF6b3SyGgCP/EcwwUGX4NG7jukhK+In9joSuAxchEg/Ba2/LVjqtfBn3hXZx/SEt+rJ0UVPIT/eEe32HflrzokNcO7l0IgyLntv5QEAsSC2hiGxrM6vF5tQpb12MVZnt1/01ytP0ruQn2TVTI96vsOAa3Cj98dAH2Z0JdqZUSVBw+o3AqXP5oeF1JWkDHZzHQjLgu741wnUZn+vVXFBu1xQyApbvH7y7cNbq8PaxU+SyZbVXbq3RwTywJsyFQvsIOM5l0tG7jUD0QAd6dP3rcNODjFTaafJaBsR9aMwvKQd/d7H+BdwFPYOFp8HB2JAzhRpvlS4Av9MCIe0474wZ0T2QOJmcs7mns= abc@123.com
```

5.将公钥添加到GitHub账号SSH设置中

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHubSSH%E7%99%BB%E5%BD%954.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHubSSH%E7%99%BB%E5%BD%955.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHubSSH%E7%99%BB%E5%BD%956.png)

6.添加公钥后，可不用输入Github账号密码便可推送代码到远程库。接下来通过SSH方式提交hello.txt。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/6GitHubSSH%E7%99%BB%E5%BD%957.png)

7.从远程仓库拉取修改过的代码，查看本地代码是否和远程代码一致。

`$ git pull git@github.com:abc/HelloGit.git master`

```
# 通过SSH拉取abc@DESKTOP-R85C9HV MINGW64 ~/Desktop/HelloGit-clone/HelloGit (master)$ git pull git@github.com:abc/HelloGit.git masterThe authenticity of host 'github.com (13.250.177.223)' can't be established.RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.Are you sure you want to continue connecting (yes/no/[fingerprint])? yesWarning: Permanently added 'github.com,13.250.177.223' (RSA) to the list of known hosts.Enumerating objects: 5, done.Counting objects: 100% (5/5), done.Delta compression using up to 8 threadsCompressing objects: 100% (2/2), done.Writing objects: 100% (3/3), 283 bytes | 283.00 KiB/s, done.Total 3 (delta 1), reused 0 (delta 0), pack-reused 0remote: Resolving deltas: 100% (1/1), completed with 1 local object.To github.com:JallenKwong/HelloGit.git   47e257f..9602a37  master -> master
```

8.将本地库修改的代码推送到远程库，查看结果：

```
Q@Moe MINGW64 /f/gitcode/h-clone/myfirst (master)$ git push git@github.com:Moe-Q/myfirst.git masterTo github.com:Moe-Q/myfirst.git ! [rejected]        master -> master (fetch first)error: failed to push some refs to 'github.com:Moe-Q/myfirst.git'hint: Updates were rejected because the remote contains work that you dohint: not have locally. This is usually caused by another repository pushinghint: to the same ref. You may want to first integrate the remote changeshint: (e.g., 'git pull ...') before pushing again.hint: See the 'Note about fast-forwards' in 'git push --help' for details.//报错在push后加 -fQ@Moe MINGW64 /f/gitcode/h-clone/myfirst (master)$ git push -f git@github.com:Moe-Q/myfirst.git masterEnumerating objects: 27, done.Counting objects: 100% (27/27), done.Delta compression using up to 4 threadsCompressing objects: 100% (12/12), done.Writing objects: 100% (27/27), 2.83 KiB | 2.83 MiB/s, done.Total 27 (delta 1), reused 21 (delta 0), pack-reused 0remote: Resolving deltas: 100% (1/1), done.To github.com:Moe-Q/myfirst.git + 9d9fa48...a1e2686 master -> master (forced update)
```

推送成功，远程代码和本地代码一致。

## 7、IDEA集成Git

### 7.1配置Git忽略文件

与项目的实际功能无关，不参与服务器上部署运行。把它们忽略掉能够屏蔽 IDE 工具之间的差异。

例如，Maven工程根据src生成的target。

创建忽略规则文件 xxxx.ignore（**前缀名随便起，建议是 git.ignore**），这个文件的存放位置原则上在哪里都可以，为了便于让`~/.gitconfig` 文件引用，建议也放在用户家目录下。

`git.ignore 文件模版内容如下：`

```
# Compiled class file*.class# Log file*.log# BlueJ files*.ctxt# Mobile Tools for Java (J2ME).mtj.tmp/# Package Files #*.jar*.war*.nar*.ear*.zip*.tar.gz*.rar# virtual machine crash logs, see http://www.java.com/en/download/help/error_hotspot.xmlhs_err_pid*.classpath.project.settingstarget.idea*.iml
```

`在.gitconfig 文件中引用忽略配置文件（此文件在 Windows 的家目录中）`

```
[user]    name = Layne    email = Layne@atguigu.com//在配置文件加如如下代码，注意：这里要使用“正斜线（/）”，不要使用“反斜线（\）”[core]	excludesfile=C:/Users/Q/git.ignore
```

### 7.2定位Git程序

在菜单栏File->Setting->搜索栏搜Git，配置Git的安装路径。并且点击test按钮出现Git版本号即为正确。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7%E9%85%8D%E7%BD%AEidea1.png)

### 7.3初始化本地库

先创建一个名叫HelloGit(名字自取)的`Maven工程`。

**初始化Git**

在菜单栏VCS -> Import into Version Control -> Create Git Repository

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7%E9%85%8D%E7%BD%AEidea2.png)

选择要创建 Git 本地仓库的工程，也就是HelloGit工程，然后添加OK。

### 7.4添加到暂存区

创建一个HelloGit类，将其添加Git暂存区。

右键点击HelloGit类，选择Git->Add。可以右键点击HelloGit，更大范围地添加文件到暂存区。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7%E9%85%8D%E7%BD%AEidea3.png)

添加成功后，文件名会从红色变成绿色。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7%E9%85%8D%E7%BD%AEidea4.png)

### 7.5提交到本地库

右键点击HelloGit，选择Git->Commit Directory。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7%E9%85%8D%E7%BD%AEidea5.png)

添加注释后提交：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7%E9%85%8D%E7%BD%AEidea6.png)

添加成功后，后台打印相关信息。

![7配置idea7.png](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7%E9%85%8D%E7%BD%AEidea7.png)

### 7.6切换版本

在 IDEA 的左下角，点击 Git，然后点击 Log 查看版本

![7idea切换版本1.png](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%88%87%E6%8D%A2%E7%89%88%E6%9C%AC1.png)

右键选择要切换的版本，然后在菜单里点击 Checkout Revision。

![7idea切换版本2.png](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%88%87%E6%8D%A2%E7%89%88%E6%9C%AC2.png)

### 7.7创建分支

右键点击HelloGit，Git -> Repository -> Branches，或者点击IDEA的右下角，如图红圈所示部位：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%88%9B%E5%BB%BA%E5%88%86%E6%94%AF1.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%88%9B%E5%BB%BA%E5%88%86%E6%94%AF2.png)

选择点击New Branch：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%88%9B%E5%BB%BA%E5%88%86%E6%94%AF3.png)

创建新分支：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%88%9B%E5%BB%BA%E5%88%86%E6%94%AF4.png)

### 7.8切换分支

跟**创建分支**步骤相似，如点击IDEA的右下角（它显示项目正处在那条分支），如图红圈所示部位，选择你想要切换的分支，然后checkout：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%88%9B%E5%BB%BA%E5%88%86%E6%94%AF2.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%88%87%E6%8D%A2%E5%88%86%E6%94%AF1.png)

或者在log窗口，右键点击分支，选择checkout：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%88%87%E6%8D%A2%E5%88%86%E6%94%AF2.png)

### 7.9合并分支

#### 7.9.1正常合并

先在hot-fix分支修改HelloGit类，并将其提交：

![7idea正常合并1.png](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E6%AD%A3%E5%B8%B8%E5%90%88%E5%B9%B61.png)

然后切换到master分支，右下角的hot-fix会变为master：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E6%AD%A3%E5%B8%B8%E5%90%88%E5%B9%B62.png)

然后，点击IDEA 窗口的右下角的master，将 hot-fix 分支合并到当前 master 分支。选择hot-fix->Merge into Current

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E6%AD%A3%E5%B8%B8%E5%90%88%E5%B9%B63.png)

如果代码没有冲突， 分支直接合并成功，分支合并成功以后，代码自动提交，无需手动
提交本地库。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E6%AD%A3%E5%B8%B8%E5%90%88%E5%B9%B64.png)

#### 7.9.2冲突合并

分别在master，hot-fix分支修改HelloGit类同一行，并提交，故意制作冲突：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%86%B2%E7%AA%81%E5%90%88%E5%B9%B61.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%86%B2%E7%AA%81%E5%90%88%E5%B9%B62.png)

切换到master分支，将hot-fix的合并到master分支：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%86%B2%E7%AA%81%E5%90%88%E5%B9%B63.png)

冲突产生，需要人工解决：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%86%B2%E7%AA%81%E5%90%88%E5%B9%B64.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%86%B2%E7%AA%81%E5%90%88%E5%B9%B65.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%86%B2%E7%AA%81%E5%90%88%E5%B9%B66.png)

代码冲突解决，将代码提交本地库后，如图所示：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/7idea%E5%86%B2%E7%AA%81%E5%90%88%E5%B9%B67.png)



## 8、IDEA集成GitHub

### 8.1设置GitHub账号

在菜单栏File->Setting->搜索栏搜GitHub，添加GitHub账号：

![8设置GitHub账号1.png](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E8%AE%BE%E7%BD%AEGitHub%E8%B4%A6%E5%8F%B71.png)

由于网络问题，会时常登陆不了：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E8%AE%BE%E7%BD%AEGitHub%E8%B4%A6%E5%8F%B72.png)

解决方法：可通过Token登陆。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E8%AE%BE%E7%BD%AEGitHub%E8%B4%A6%E5%8F%B73.png)

登陆Github网站，**获取Token**，操作步骤看下图：

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E8%AE%BE%E7%BD%AEGitHub%E8%B4%A6%E5%8F%B74.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E8%AE%BE%E7%BD%AEGitHub%E8%B4%A6%E5%8F%B75.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E8%AE%BE%E7%BD%AEGitHub%E8%B4%A6%E5%8F%B76.png)

将生成的token用来IDEA登录。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E8%AE%BE%E7%BD%AEGitHub%E8%B4%A6%E5%8F%B77.png)

### 8.2分享工程到GitHub

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E5%88%86%E4%BA%AB%E5%B7%A5%E7%A8%8B%E5%88%B0GitHub1.png)

### 8.3push推送本地库到远程库

注意： push 是将本地库代码推送到远程库，如果本地库代码跟远程库代码版本不一致，
push 的操作是会被拒绝的。也就是说， 要想 push 成功，一定要保证**本地库的版本要比远程库的版本高**！ 因此一个成熟的程序员在动手改本地代码之前，一定会先检查下远程库跟本地代码的区别！如果本地的代码版本已经落后，切记要先 pull 拉取一下远程库的代码，将本地代码更新到最新以后，然后再修改，提交，推送！

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E6%8E%A8%E9%80%81GitHub1.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E6%8E%A8%E9%80%81GitHub2.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E6%8E%A8%E9%80%81GitHub3.png)

### 8.4pull拉取远程库到本地库

右键点击项目，可以将远程仓库的内容 pull 到本地仓库。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E6%8B%89%E5%8F%96GitHub1.png)

注意： pull 是拉取远端仓库代码到本地，如果远程库代码和本地库代码不一致，会自动
合并，如果自动合并失败，还会涉及到手动解决冲突的问题。

### 8.5clone克隆远程库到本地库

在菜单栏的File->Close Project->Get from Version Control。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E5%85%8B%E9%9A%86GitHub1.png)

或者在菜单栏VCS->Get from Version Control。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/8%E5%85%8B%E9%9A%86GitHub2.png)

## 9、国内代码托管中心-码云

### 9.1码云简介

众所周知， GitHub 服务器在国外， 使用 GitHub 作为项目托管网站，如果网速不好的话，严重影响使用体验，甚至会出现登录不上的情况。针对这个情况， 大家也可以使用国内的项目托管网站-码云。

码云是开源中国推出的基于 Git 的代码托管服务中心， 网址是 https://gitee.com/ ，使用
方式跟 GitHub 一样，而且它还是一个中文网站，如果你英文不是很好，它是最好的选择。

### 9.2创建远程库

跟Github的类似。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/9%E7%A0%81%E4%BA%911.png)

另外，可以从GitHub与GitLab中导入仓库。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/9%E7%A0%81%E4%BA%912.png)

### 9.3IDEA集成Gitee码云

首先，要在IDEA安装Gitee插件。

在菜单栏选File->Settings->Plugins，搜Gitee。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/9%E7%A0%81%E4%BA%913.png)

安装插件成功后，重启IDEA。

功能跟在IDEA的Github插件，功能类似，如添加Gitee账号等，可参考前文IDEA的Github插件。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/9%E7%A0%81%E4%BA%914.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/9%E7%A0%81%E4%BA%915.png)

### 9.4码云复制GitHub项目

新建仓库，选择点击导入

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/9Gitee%E5%A4%8D%E5%88%B6GitHub%E9%A1%B9%E7%9B%AE1.png)

输入GitHub链接等待导入完成

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/9Gitee%E5%A4%8D%E5%88%B6GitHub%E9%A1%B9%E7%9B%AE2.png)

GitHubub上更新了，gitee上可以点击如下图标实现同步更新。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/9Gitee%E5%A4%8D%E5%88%B6GitHub%E9%A1%B9%E7%9B%AE3.png)

![](9Gitee复制GitHub项目4.png)

## 10、自建代码托管平台—GitLab

### 10.1GitLab简介

GitLab 是由 GitLab Inc.开发，**使用 MIT 许可证的基于网络的 Git 仓库管理工具**，且具有wiki 和 issue 跟踪功能。使用 Git 作为代码管理工具，并在此基础上搭建起来的 web 服务。（可搭建局域网Git仓库）。

GitLab 由乌克兰程序员 DmitriyZaporozhets 和 ValerySizov 开发，它使用 Ruby 语言写成。后来，一些部分用 Go 语言重写。截止 2018 年 5 月，该公司约有 290 名团队成员，以及 2000 多名开源贡献者。 GitLab 被 IBM， Sony， JülichResearchCenter， NASA， Alibaba，Invincea， O’ReillyMedia， Leibniz-Rechenzentrum(LRZ)， CERN， SpaceX 等组织使用。

### 10.2GitLab官方网址

官方网址：`https://about.gitlab.com/`

安装说明：`https://about.gitlab.com/install/`

### 10.3GitLab安装

#### 10.3.1服务器准备

1. 如准备一个系统为 CentOS7 以上版本的服务器， 要求内存 4G，磁盘 50G。
2. 关闭防火墙， 并且配置好主机名和 IP，保证服务器可以上网。
3. 此教程使用虚拟机：主机名： gitlab-server IP 地址： 192.168.6.200
4. Yum 在线安装 gitlab- ce 时，需要下载几百 M 的安装文件，非常耗时，所以最好提前把所需 RPM 包下载到本地，然后使用离线 rpm 的方式安装。

#### 10.3.2安装包准备

**下载地址：**

 **gitlab / gitlab-ce / el / 7：**

```
https://packages.gitlab.com/gitlab/gitlab-ce/packages/el/7/gitlab-ce-13.10.2-ce.0.el7.x86_64.rpm
```

注：资料里提供了此 rpm 包，直接将此包上传到服务器/opt/module 目录下即可。

#### 10.3.3编写安装脚本

安装 gitlab 步骤比较繁琐，因此我们可以参考官网编写 gitlab 的安装脚本：

```
https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh
```

```
[root@gitlab-server module]# vim gitlab-install.sh
sudo rpm -ivh /opt/module/gitlab-ce-13.10.2-ce.0.el7.x86_64.rpm //离线安装gitlab-ce

sudo yum install -y curl policycoreutils-python openssh-server cronie

sudo lokkit -s http -s ssh

sudo yum install -y postfix

sudo service postfix start

sudo chkconfig postfix on

curl https://packages.gitlab.com/install/repositories/gitlab/gitlabce/script.rpm.sh | sudo bash

sudo EXTERNAL_URL="http://gitlab.example.com" yum -y install gitlabce
```

给脚本增加执行权限

```
[root@gitlab-server module]# chmod +x gitlab-install.sh
[root@gitlab-server module]# ll
总用量 403104
-rw-r--r--. 1 root root 412774002 4 月 7 15:47 gitlab-ce-13.10.2-
ce.0.el7.x86_64.rpm
-rwxr-xr-x. 1 root root 416 4 月 7 15:49 gitlab-install.sh
```

然后执行该脚本，开始安装 gitlab-ce。注意一定要保证服务器可以上网。

```
[root@gitlab-server module]# ./gitlab-install.sh
警告： /opt/module/gitlab-ce-13.10.2-ce.0.el7.x86_64.rpm: 头 V4
RSA/SHA1 Signature, 密钥 ID f27eab47: NOKEY
准备中... #################################
[100%]
正在升级/安装...
1:gitlab-ce-13.10.2-ce.0.el7
################################# [100%]
。 。 。 。 。 。
```

#### 10.3.4初始化GitLab服务

执行以下命令初始化 GitLab 服务，过程大概需要几分钟，耐心等待…

```
[root@gitlab-server module]# gitlab-ctl reconfigure //初始化GitLab服务。 。 。 。 。 。Running handlers:Running handlers completeChef Client finished, 425/608 resources updated in 03 minutes 08secondsgitlab Reconfigured!（初始化成功）
```

#### 10.3.5启动GitLab服务

执行以下命令启动 GitLab 服务，如需停止，执行 `gitlab-ctl stop`

```
[root@gitlab-server module]# gitlab-ctl start
ok: run: alertmanager: (pid 6812) 134s
ok: run: gitaly: (pid 6740) 135s
ok: run: gitlab-monitor: (pid 6765) 135s
ok: run: gitlab-workhorse: (pid 6722) 136s
ok: run: logrotate: (pid 5994) 197s
ok: run: nginx: (pid 5930) 203s
ok: run: node-exporter: (pid 6234) 185s
ok: run: postgres-exporter: (pid 6834) 133s
ok: run: postgresql: (pid 5456) 257s
ok: run: prometheus: (pid 6777) 134s
ok: run: redis: (pid 5327) 263s
ok: run: redis-exporter: (pid 6391) 173s
ok: run: sidekiq: (pid 5797) 215s
ok: run: unicorn: (pid 5728) 221s
```

#### 10.3.6使用浏览器访问GitLab

1.过浏览器输入自己设置的IP地址访问(端口号默认:80)。![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/10%E6%B5%8F%E8%A7%88%E5%99%A8%E8%AE%BF%E9%97%AEGitLab1.png)

2.可以通过主机名的方式访问，需要提前在Windows中的hosts中配置了主机名的映射。

```
(C:\Windows\System32\drivers\etc)
```

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/10%E6%B5%8F%E8%A7%88%E5%99%A8%E8%AE%BF%E9%97%AEGitLab2.png)

3.首次登陆之前，需要修改下 GitLab 提供的 root 账户的密码，要求 8 位以上，包含大小写子母和特殊符号。

然后使用修改后的密码登录 GitLab。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/10%E6%B5%8F%E8%A7%88%E5%99%A8%E8%AE%BF%E9%97%AEGitLab4.png)

#### 10.3.7GitLab创建远程库

创建远程库

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/10%E6%B5%8F%E8%A7%88%E5%99%A8%E8%AE%BF%E9%97%AEGitLab5.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/10%E5%88%9B%E5%BB%BA%E8%BF%9C%E7%A8%8B%E5%BA%93GitLab1.png)

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/10%E5%88%9B%E5%BB%BA%E8%BF%9C%E7%A8%8B%E5%BA%93GitLab2.png)

#### 10.3.8IDEA集成GitLab

安装插件配置，Git操作等与Github、Gitee的IDEA插件大同小异。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/10IDEA%E9%9B%86%E6%88%90GitLab1.png)

输入相关账号信息登录，登录成功有账号显示在上面。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/10IDEA%E9%9B%86%E6%88%90GitLab2.png)

选中http链接，如果链接里面的不是自己的主机名，需要把其换成自己的主机名。

![](https://gitee.com/Moe-Q/gitee-images/raw/main-img/images/10IDEA%E9%9B%86%E6%88%90GitLab3.png)

后续相应操作和GitHub一样。

