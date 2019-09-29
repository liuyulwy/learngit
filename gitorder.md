 [git init](#git init) 

 [git remote](#git remote)

 [git clone](#git clone)

 [git status](#git status)

 [git add](#git add)

 [git commit](#git commit)

 [git stash](#git stash)

 [git log](#git log)

 [git shortlog](#git shortlog)

 [git reflog](#git reflog)

 [git checkout](#git checkout)

 [git reset](#git reset)

 [git revert](#git revert)

 [git rm](#git rm)

 [git mv](#git mv)

 [git branch](#git branch)

 [git fetch](#git fetch)

 [git pull](#git pull)

 [git push](#git push)

 [git merge](#git merge)

 [git tag](#git tag)

[git diff](#git diff)



[test点击](#test)

## 常用git 命令

#### git init

```tex
git init 现有项目初始化 生成 .git文件 在该文件夹默认会创建master分支
git remote add 别名（origin）仓库地址url  关联远程仓库,并将本地的master分支跟踪到远程的分支
```

#### git remote

``````tex
git remote 它会列出每个远程库的简短名字
git remote -v 显示对应的克隆地址
git remote add 别名（origin）仓库地址url  关联远程仓库,并将本地的master分支跟踪到远程的分支
git remote show origin 查看远程仓库信息
git remote rename oldname newname 修改某个远程仓库在本地的简称
git remote rm name 除对应的远端仓库
``````

#### git clone

```tex
git clone url 本质上就是自动创建了本地的 master 分支用于跟踪远程仓库中的 master 分支,自动将远程仓库归于 origin 名下
```

#### git status

```tex
git status 检查当前文件状态
git status -s 或 git status --short 简洁显示
?? 新添加的未跟踪文件
M 表示该文件被修改了但是还没放入暂存区
A 新添加到暂存区中的文件
```

#### git add 

```tex
可以用它开始跟踪新文件，或者把已跟踪的文件放到暂存区，还能用于合并时把有冲突的文件标记为已解决状态等
git add <file> 将指定文件放入暂存区
git add <directory> 将指定目录下所有变化的文件，放入暂存区
git add . 将当前目录下所有变化的文件，放入暂存区，等同于git add -A
git add -u 表示只添加暂存区已有的文件（包括删除操作），但不添加新增的文件。
git add -f <fileName> 表示强制添加某个文件，不管.gitignore是否包含了这个文件。
```

#### git commit 

```tex
用于将暂存区中的变化提交到仓库区。
git commit -m "message" message用于添加提交说明。
git commit <filename>  -m "message" 命令可以跳过暂存区，直接将文件从工作区提交到仓库区。先添加到暂存区，然后再将暂存区提交到仓库区。
git commit -am "message" 用于先将所有工作区的变动文件，提交到暂存区,再运行git commit
git commit -a 如果没有指定提交说明，运行下面的命令会直接打开默认的文本编辑器，让用户撰写提交说明。
git commit --allow-empty 用于没有提交信息的 commit。
git commit --amend -m "new commit message" 用于撤销上一次 commit，然后生成一个新的 commit。
git commit --fixup <commit> 当前添加的 commit 是以前某一个 commit 的修正。以后执行互动式的git rebase的时候，这两个 commit 将会合并成一个。
git commit --squash <commit> 参数的作用与--fixup类似，表示当前添加的 commit 应该与以前某一个 commit 合并成一个，以后执行互动式的git rebase的时候，这两个 commit 将会合并成一个。
```

#### git stash

``````tex
git stash命令用于暂时保存没有提交的工作。运行该命令后，所有没有commit的代码，都会暂时从工作区移除，回到上次commit时的状态。
git stash list 列出所有暂时保存的工作
git stash apply stash@{1} 恢复某个暂时保存的工作,不会自动删除取出的修改，需要手动删除。
git stash pop 恢复最近一次stash的文件,自动删除stash
git stash drop 丢弃最近一次stash的文件
git stash drop stash@{1} 丢弃某个暂时保存的工作
git stash clear 删除所有的stash
git stash branch stashdev 以stash创建分支
``````

#### git log

```tex
git log 列出当前分支的版本历史
git log --follow [file] 列出某个文件的版本历史，包括文件改名
git log origin/master | git log master 查看远程分支/分支的变动情况。
git log -i --author=ly 查找log，即搜索commit的开发者为ly信息。-i忽略大小写
git log -i --grep="message" 查找提交信息为"message"的日志
git log commitid(old)..commitid(new) 查看某个范围内的commit
git log -p master..origin/master 比较本地的master分支和origin/master分支的差别
git log --graph --decorate --pretty=oneline --abbrev-commit 格式化输出
git log --graph --oneline 同上
git log --oneline -5 显示5条
—graph commit之间将展示连线
—decorate 显示commit里面的分支
—pretty=oneline 只显示commit信息的标题
—abbrev-commit 只显示commit SHA1的前7位
```

#### git shortlog

``````tex
git shortlog -s -n git #repository 底下每个用户进行 commit 的次数，以及每次 commit 的注释
-s 参数省略每次 commit 的注释，仅仅返回一个简单的统计。
-n 参数按照 commit 数量从多到少的顺序对用户进行排序
``````

#### git reflog

``````tex
git reflog -n 查看命令历史，以便确定要回到未来的哪个版本。
``````

#### git checkout 

```tex
git checkout develop 表示切换到develop分支。
git checkout -b dev  切换并创建dev分支
git checkout -b dev origin/dev 切换并创建dev分支从远程dev
git checkout -b dev commitid/tag 从ID或tag上切换创建分支dev
git checkout <commitID> 切换到指定快照（commit）是不能更改它的代码的,更改了代码也不会在其他分支上体现，
“--”貌似没什么用加不加都行
git checkout -- <filename> 用来丢弃工作区对该文件的修改 gitcheckout <filename>也可以
git checkout . 或 git chekcout -- .  丢弃工作区所有修改
git checkout HEAD~ -- <filename> 还可以指定从某个 commit 恢复指定文件，这会同时改变暂存区和工作区
git checkout commitid <filename> 同上 
git checkout tags/1.1.4 或 git checkout 1.1.4 切换到某个tag 只是一个快照detached HEAD状态
```

#### git reset

```tex
如果不指定回滚的位置，那么等同于撤销修改。
git reset 撤销上一次向暂存区添加的所有文件
git reset --soft 无任何效果
git reset --hard 同时撤销暂存区和工作区的修改 回复到上一次提交的状态
git reset -- <filename> 撤销上一次向暂存区添加的某个指定文件，不影响工作区中的该文件
git reset HEAD~3 将当期分支的指针倒退三个 commit，并且会改变暂存区
git reset --soft HEAD~3 倒退指针的同时，不改变暂存区 此次之后的修改都会被退回到暂存区
git reset --hard HEAD~3 倒退指针的同时，改变工作区

soft: 不改变工作区和缓存区，只移动 HEAD 到指定 commit。
mixed: 只改变缓存区，不改变工作区。***这是默认参数***，通常用于撤销git add。
hard：改变工作区和暂存区到指定 commit。该参数等同于重置，可能会引起数据损失。git reset --hard等同于git reset --hard HEAD。
-p表示键入交互模式，指定暂存区的哪些部分需要撤销。
```

#### git revert

``````tex
git revert 是生成一个新的提交来撤销某次提交，此次提交之前的commit都会被保留
``````

区别 ： git reset 是回到某次提交，提交及之前的commit都会被保留，但是此次之后的修改都会被退回到暂存区

#### git rm

``````tex
git rm filename 同时从工作区和索引中删除文件。即本地的文件也被删除了。
git rm --cached filename 从索引中删除文件。但是本地文件还存在， 只是不希望这个文件被版本控制。解除追踪某个文件，即该文件已被git add添加，然后抵消这个操作
git rm -r --cached file 从索引中删除文件夹，本地存在
rm filename 物理删除文件 不会在git中记录
rm -r 删除文件夹
``````

#### git mv

``````tex
git mv text.txt mydir 把一个文件：text.txt 移动到 mydir，可以执行以下操作
运行上面的 git mv 其实就相当于运行了3条命令
mv test.txt mydir/
git rm test.txt
git add mydir
``````

#### git branch

``````tex
git branch 列出所有本地分支
git branch -r  列出所有远程分支
git branch -a 列出所有本地分支和远程分支
git branch develop 新建一个分支，指向当前 commit
git checkout -b NewBranch MyBranch 可以新建的同时，切换到新分支。
git branch -d <分支名> 删除一个分支
git branch -D <分支名> 强制删除一个分支，不管有没有未合并变化。
git push origin --delete <分支名> 删除远程分支
git branch -m devname 为当前分支改名
git branch -m 原名字 新名字 为指定分支改名
git branch -m feature132 twitter-experiment 如果有重名分支，强制改名
git branch --set-upstream-to=origin/master master 设置当前分支与远程分支存在追踪关系 之后通过git pull git push 直接拉取或提交
``````

#### git fetch

``````tex
git fetch 相当于是从远程获取最新到本地，不会自动merge
git fetch orgin master //将远程仓库的master分支下载到本地当前branch中
git log -p master..origin/master //比较本地的master分支和origin/master分支的差别
git merge origin/master //进行合并

git fetch origin master:tmp //从远程仓库master分支获取最新，在本地建立tmp分支
git diff tmp //將當前分支和tmp进行对比
git merge tmp //合并tmp分支到当前分支
``````

#### git pull

``````tex
git pull <远程主机名> <远程分支名>:<本地分支名> 取出远程分支数据并合并到本地分支中，如果本地无分支，会自动创建分支。相当于git fetch 再 git merge，“：分支名”可省略 表示当前分支
git pull origin develop  拉取远程分支到当前本地分支。
git pull --rebase <远程主机名> <远程分支名>:<本地分支名> 相当于 git fetch 再 git rebase
git branch --set-upstream-to=origin/master master 设置当前分支与远程分支存在追踪关系 之后通过git pull 直接拉取远程分支到本地
``````

#### git push

``````tex
git push <远程主机名> <本地分支名>:<远程分支名> 命令用于将本地分支的更新，推送到远程主机
git push origin master 将本地的master分支推送到origin主机的master分支。如果master不存在，则会被新建
git push origin :master 等同于 git push origin --delete master 表示删除origin主机的master分支
git push origin --tags 推送tag
git push origin tag_name 推送tag
git push origin :tag_name 删除远程标签
``````

#### git merge 

``````tex
git merge dev 将分支dev合并到当前分支中，自动进行新的提交
git merge --no-commit dev 合并到当前分支中，但不要自动进行新的提交,手动提交并写提交信息
git merge --no-ff dev 即使可以使用fast-forward模式，也要创建一个新的合并节点。
git merge --squash dev 当一个合并发生时，从当前分支和对方分支的共同祖先节点之后的对方分支节点，一直到对方分支的顶部节点将会压缩在一起，使用者可以经过审视后进行提交，产生一个新的节点。
功能分支在进行一个功能需求的研发时，开发者可能在本地提交了大量且无意义的节点，当需要合并到develop分支时，可能仅仅需要用一个新的节点来表示这一长串节点的修改内容，这时--squash命令将会发挥作用。此外，如果功能分支的多次提交并不是琐碎而都是有意义的，使用--no-ff命令更为合适。
``````

#### git tag

``````tex
git tag 列出现有标签
git tag -l 'v1.0.*' 列出v1.0.*系列标签
git tag name 轻量级标签
git tag -a v1.4 -m 'my version 1.4' 含附注的标签
git tag -a v1.2 commitid -m "des" 后期添加标签
git show v1.4 查看相应标签的版本信息
git tag -d v1.0 删除本地标签
git push origin :refs/tags/test_tag 或 git push origin --delete tag v1.2.0 删除远程tag
git push origin --tags 推送所有标签到远程
git push origin v1.5 推送到远程
``````

#### git diff

``````tex
git diff 工作目录和暂存区之间的差异
git diff <file>  比较当前文件和暂存区文件差异
git diff --cached | git diff --staged 已经暂存起来的文件(staged)和上次提交时的快照之间(HEAD)的差异
git diff HEAD 工作区和暂存区 与 已经提交版本库的差异
git diff test 查看当前目录和另外一个分支(test)的差别
git diff dev1 dev2 | git diff dev1..div2 两个分支上最新的提交做diff
git diff --stat 查看简单的diff结果
git diff HEAD^ HEAD 比较上次提交和上上次提交
git diff commitid commitid 比较两个历史版本之间的差异
``````

#### test