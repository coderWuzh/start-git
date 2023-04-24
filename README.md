#### 1.安装

#### 2.配置：

name

```bash
  git config --global user.name "wuzhenhua"	
```

email

```bash
 git config --global user.email "1504966697@qq.com"
```

#### 3.使用git：

查看当前查看的状态

```bash
git status
```

初始化仓库

```bash
git init
```

刚刚添加到项目中的文	件是未跟踪状态
未跟踪 --> 暂存

```bash
git add filename  #将文件切换到暂存状态
git add * #将所有已修改(未跟踪)的文件暂存
```


暂存 --> 未修改

```bash
git commit -m "xxx" #将暂存的文件存储到仓库中
git commit -a -m "xxx" #提交所有已修改的文件(未跟踪的不会提交)
```

未修改 --> 修改
修改代码后，文件会变为修改状态

#### 4.常用命令

1.重置文件

```	bash
git restore <filename> #恢复文件
git restore --staged <filename> #取消暂存状态
```

2.删除文件

```bash
git rm <filename>
git rm <filename> -f  #强制删除
```

3.移动文件

```bash
git mv from to  #移动文件 重命名文件
```

#### 分支

git在存储文件是，每一次代码的提交都会创建一个与树对应的节点，git就是通过一个个的节点来记录代码的状态，节点会构成一个树状结构。树状结构就意味着这个树会存在分支，默认情况下仓库只有一个分支，命名为master。在使用git时，可以创建多个分支，分支与分支之间相互独立，互不影响。

```bash
git branch #查看当前分支
git branch <branch name> #创建新的分支
git branch -d <branch name> #删除分支
git switch <brach name> #切换分支
git switch -c <branch name> #创建并切换分支
```

在开发中，都是在自己的分支上编写代码，代码编写完成后，在将自己的分支合并到主分支中

```bash
git merge <branch name> #合并分支到master,需要先切换回master分支
```

#### 变基(rebase)

在开发中除了通过merge来合并分支外，还可以用过变基来完成分支的合并。

通过merge合并分支时，在提交记录中会将所有的分支创建和分支的合并的过程都显示出来，这样当项目较为复杂时，开发过程比较波折时，我们必须要反复的创建、合并、删除分支。这样一来将会使得我们代码的提交记录极其混乱。

原理（变基时发生了什么）：

1. 当我们发起变基时，git会首先找到两条分支的最近的共同祖先
2. 对比当前分支相对于祖先的历史提交，并且将他们提取到临时储存里
3. 将当前部分执行目标的基底
4. 以当前基底开始，重新执行历史操作

变基和merge对于合并分支来说结果运用，但是代码的提交记录更为整洁清晰。

注意：大部分情况下合并和变基时可以互换的，但是如果分支以及提交给了远程操控，name这是尽量不要使用变基。

#### 远程仓库(remote)

远程仓库可以多人使用，方便协同开发。实际工作中，git服务器通常由公司搭建内部使用或者购买一些公共的私有git服务器。学习阶段直接使用一些公共的git仓库。目前常用的库有两个：GitHub和Gitee(码云)

将本地库上传到GitHub:

```bash
git remote add origin https://github.com/wuzhenhua666/gitdemo.git
#git remote add <remote name> <url>

git branch -M main
#修改分支的名字为main

git push -u origin main
#git push 将代码上传到服务器
```

将本地库上传到Gitee:

```bash
cd existing_git_repo

git remote add gitee https://gitee.com/wu_zhenhua/gitdemo.git

git push -u gitee main

```





