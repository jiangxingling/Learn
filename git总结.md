#Github简介
----------------------

##一、项目下各模块简介  

* **Code**  
项目的代码文件，对项目的介绍通常在README.md文件中，需要使用markdown语法

* **Issues**  
代表项目的一些问题或bug.可以通过"New issue"来创建Issue，添加标题与描述

* **Pull Requests**  
用来向项目中提交修改。首先Fork到自己的Repository里，把该项目clone到本地，修改后再从本地push到github，点击New Pull Request按钮提交

* **Projects**  
方便把Issues、Pull、requests进行分类
 
* **Wiki**  
遇到一些复杂的项目时，可以在这里提供详细的使用说明文档

* **Pulse**  
展现该仓库最近创建了多少个Pull request或Issue，通过这个页面可以判断该项目的活跃程度  

* **Graphs**  
以图表的形式来展示该项目的整体情况  

* **Settings**  
仅在自己的项目下才有，该菜单包括对整个项目的设置信息，如对项目重命名，删除该项目等  

# Git简介  
----------------
## 一、几个基本概念  

* **工作区和暂存区**  
工作区：相当于本地工作环境，是电脑上能看到的目录。  
暂存区：工作区中的.git目录就是版本库，其中的index就是暂存区，.git目录下包括git为我们自动创建的分支master,HEAD就是指向master的指针。  
git add 就是将文件添加到暂存区，git commit是将文件修改提交到分支  
git diff HEAD    ——查看工作空间与本地库之间的差异  
git diff --staged   ——查看暂存区与本地库之间的差异  
git reset xx.txt    ——重置暂存区中的文件  

* **远程仓库**  
由github来充当远程仓库的角色，添加ssh key确保向github提交的信息是由自己提交的  

# 常用操作  
---------------
## 一、创建远程仓库  
进入 github，点击 New repository，输入Repository name，添加必要的说明并新建即可。

## 二、克隆远程仓库到本地 
### 1）git 环境配置，添加ssh key  
* 生成本地ssh key
> ssh-keygen -t rsa -C "邮箱"     

后面一路回车即可，执行完毕后，会生成一个 id_rsa.pub 文件，该文件默认路径在 C:\Users\Adaministrator\.ssh  

* 将 SSH key 添加到 github  
回到github上，进入 Account Settings，左边选择SSH Keys，Add SSH Key,title随便填，粘贴id_rsa.pub 文件里面的内容

### 2）git 初次配置用户名和邮箱  
在首次提交前，需要配置账号名和邮箱，这个配置在每次 git commit 都会使用到，只有首次使用 git 才需要配置，命令如下：
> git config --global user.name "用户名"  
> git config --global user.email "邮箱"

### 3）关联远程仓库  
我们可以为一个本地库添加多个远程仓库，方便将本地代码推送到不同远程仓库中。进入要关联的本地项目下，执行命令：
> git remote add test master git@github.com:xxx/xxx.git  

关联之后远程仓库的名字就叫做 test  
如果关联时报错：remote origin already exists  
解决办法： 
> git remote rm origin

### 4）克隆项目到本地  
进入本地要存放项目的目录下，执行如下命令
> git clone git@github.com:xxx/xxx.git

## 三、在本地进行开发 

## 四、提交修改  
> git status       
> git add 文件名  
> git commit -m "修改说明"  

## 五、将修改合并到远程仓库  
> git push test master  

大多数情况下，我们都是在一个远程分支上进行代码提交，所以可以将远程分支与本地分支关联，第一次 push 时，使用
> git branch --set-upstream-to test master  

在后面再提交时，直接使用
> git push

# Git 常用操作  
| 命令   |   说明 |  
|--------|----------------|  
| pwd | 查看当前路径  |  
| mkdir <FolderName> | 创建新文件夹 |  
| cd <FolderName> | 进入文件夹目录下 |  
| git init | 生成 .git 文件夹，创建一个空的Git仓库或重新初始化一个现有仓库 |  
| ls -a | 列出目录中的所有项（包括隐藏项） |  
| git add <FileName> | 把文件添加到暂存区 |  
| git commit -m "说明" | 将文件提交到分支，添加提交信息，提交成功后提示有几个文件被改动 |  
| git status | 查看状态（哪些文件被改动过但没有提交） |  
| git diff <FileName> | 查看修改的具体内容 |  
| git diff HEAD -- <FileName> | 查看文件在版本库和工作区中的区别 |  
| git log | 查看近几次的 commit 信息 |  
| git log --pretty=oneline | 查看由近到远的 commit 信息 |  
| git reset --hard HEAD^ | 回退到上一个版本<br>HEAD表示当前版本，HEAD^表示上一个版本<br>往上 n 个版本可以写成HEAD~n |
| git reset --hard <ID> | 回到指定版本 |  
| cat <FileName> | 查看文件内容 |  
| git reflog | 查看每一次操作，包括回退版本的id |  
| git checkout -- <FileName> | 撤回修改<br>修改后的文件在暂存区，则回到 git add 前的状态<br>修改后的文件没有放在暂存区，则回到和版本库一样的状态 |  
| git reset HEAD <FileName> | 将暂存区的文件回退到工作区 |  
| 小结 |场景1：修改错误的文件在工作区，还没有提交到暂存区，使用git checkout -- <FileName><br>
场景2：修改错误的文件已经add到暂存区，先使用 git reset HEAD <FileName> 回退到工作区，再使用git checkout -- <FileName><br>
场景3：修改错误的文件已经commit，使用git reset -- hard HEAD^ 回退到上一个版本 |  
| git rm <FileName> | 删除文件 |  
| git checkout -b <branchName> | 创建并切换到分支 |  
| git merge <branchName> | 合并指定分支到当前分支 |  
| git branch -d <branchName> | 删除指定分支 |  
