# git基础使用

```sh
git config --global user.name 'rayfengleixing'
git config --global user.email 290844480@qq.com

git clone git@github.com:rayfengleixing/notes.git   # 得到文件夹 notes/ 

git init	#初始化当前目录变成Git可以管理的仓库

# 添加/修改 文件
git add file1 file2 ... 	# 添加f1.f2..到仓库
git commit -m '操作说明' 

# 删除（先删除本地）
git rm file1 file2 ...
git commit -m '操作说明'

git status 	# 查看暂存区情况
git diff	# 查看文件修改前后变化
git push -f		# 强制覆盖push  

# 有时候，commit完成后发现漏掉几个文件没有添加，或信息写错了，就需要对操作进行撤销。
git commit --amend
git add file1 file2
git commit -m 'xxxxx'

git remote add origin git@github.com:rayfengleixing/notes.git
git push -u origin master 	# 第一次需要账号密码，以后 commit 完直接 git push

# 版本回退
git log [--pretty=online]
git reset commit_id / HEAD[^]
git checkout filename
```

详细用法参考：

- [Git廖雪峰](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

### **git fetch和git pull的区别**

1. *git fetch*：相当于是从远程获取最新版本到本地，不会自动合并。

```shell
$ git fetch origin master
$ git log -p master..origin/master
$ git merge origin/master
```

以上命令的含义：

- 首先从远程的`origin`的`master`主分支下载最新的版本到`origin/master`分支上
- 然后比较本地的`master`分支和`origin/master`分支的差别
- 最后进行合并

上述过程其实可以用以下更清晰的方式来进行（**完整的过程**）：

```shell
$ git remote -v				# 查看远程地址
$ git fetch origin master:tmp	# fetch命令拉取远程仓库主分支到本地tmp作为暂存分支
$ git branch				# 查看当前指针指向的是哪个分支,*代表当前分支
$ git diff tmp 				# 查看远程与本地之间的区别
$ git merge tmp				# merge命令，将远程拉下来的tmp分支与本地分支进行合并
$ git push origin master	# 版本合并统一后，push远程仓库代码
$ git branch -d tmp			# 删除暂存分支
$ git branch				# 再次查看本地分支，已经删除，操作完毕
```

2. *git pull*：相当于是从远程获取最新版本并`merge`到本地 

```shell
git pull origin master
```

上述命令其实相当于`git fetch` 和 `git merge`
在实际使用中，`git fetch`更安全一些，因为在`merge`前，我们可以查看更新情况，然后再决定是否合并。

