# git常用Bash操作：

## clone git仓库
```
$ git clone git@github.com:Aaronzmia/Start.git
Cloning into 'Start'...
Enter passphrase for key '/c/Users/Jelly/.ssh/id_rsa':
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (3/3), done.
```

## 查看状态：
````
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
```

## 提交：
```
$ touch <文件名>：Untracked files
$ git add <文件名>: 加入缓存区域，向暂存区添加文件，Changes to be committed:
$ git commit -m "注释"：提交到github
	-m：提交信息
```

## 查看日志：
```
$ git log 
	--pretty=short：只显示第一行简述信息，注释信息
	<目录、文件>：只显示该目录下或该文件相关的日志
	-p <目录、文件>：查看提交所带来的改动
```

## 查看更改前后的差异：工作树、暂存区、最新提交
```
git diff
	HEAD：add提交后，查看工作树和最新提交的差别；HEAD是指向当前分支中最新一次提交的指针
	HEAD^：上一版本
	HEAD^^
	注：
		+：新添加
		-：已删除
```
	
## Push，更新github：
$ git push

## 新建并初始化仓库：
```
$ mkdir <目录名>
$ cd <目录名>
$ git-init
初始化成功，该目录下生成.git目录，此目录存储着管理当前目录内容所需的仓库数据；“附属于该仓库的工作树”，文件的编辑等操作在工作树中进行，  
然后记录到仓库中，以此管理文件的历史快照，如果想要恢复到原先的状态，以此管理文件的历史快照，在工作树中打开；开发者可以通过此来获取以往的文件；
```

## 丢弃工作区的修改：
```
$ git checkout -- <file>
```

## 删除版本库中的文件：
```
$ git rm <文件名>
$ git commit 
```

## 恢复：只能恢复到最新版本，会丢失最近一次提交后修改的内容
```
$ git checkout -- <文件名>
```


# 分支的相关操作：

## 显示分支：
```
$ git branch
```

## 创建切换分支：
```
$ git checkit -b <名称>：等同于执行git branch <名称>，gitcheckout<名称>
    注：分支的提交不会改变master的文件
### 特性分支：topic分支，集中实现单一特性，除此之外不进行任何作业的分支；开发中，通常可以创建多个特性分支，保持一个随时可以发布软件的稳定分支；  
稳定分支通常由master分支担当；
代码仅提交到分支
```

## 合并分支：
```
$ git merge <分支名>
	--no-ff
```

## 删除分支：
```
$ git branch -d <分支名>
```

## 以图表形式查看分支：以图表方式输出提交日志
```
$ git log --graph
```

# 更改提交的操作：
## 回溯历史版本：
```
$ git reset
```

## 回溯到创建feature-A分支前：
```
$ git rest --hard <目标时间点的hash值>
```

## 查看当前仓库执行过的操作日志：
```
$ git reflog：只要不进行git的GC操作，就可以通过日志随意调取近期的历史状态；
```

## 解决多分支提交冲突：必须首先解决冲突。解决冲突后，再提交，合并完成
	提交后，进行更改，Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容；

## 修改提交信息:
```
$ git commit --amend
```

## 分支管理策略：
```
合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会丢掉分支信息。如果要强制禁用Fast forward模式，Git就会在merge时生成  
一个新的commit，这样，从分支历史上就可以看出分支信息；
--no-ff模式：禁用Fast forward，普通模式；合并后的历史有分支，能看出曾经做过合并，而fast forward合并就看不出来曾经做过合并；

master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；
dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版
个人分支合并到dev分支，再合并到master
```


## 添加远程库：
```
$ git remote add origin git@github.com:<用户名>/<>.git：
	把一个已有的本地仓库与之关联，然后，把本地仓库的内容推送到GitHub仓库
$ git push -u origin master：
	把本地库的所有内容推送到远程库上
	-u：把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来
本地作了提交，把本地master分支的最新修改推送至GitHub：
$ git push origin master
```

## 克隆远程库
```
$ git clone git@github.com:<用户名>/<库名>.git
Git支持多种协议，包括https，但通过ssh支持的原生git协议速度最快
```




