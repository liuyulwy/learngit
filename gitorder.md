## 常用git 命令

* 现有项目初始化 生成 .git文件

  ```tex
  git init
  ```

* 克隆现有仓库

  ```tex
  git clone url
  ```
  
* 检查当前文件状态
  
  ```tex
  git status
  git status -s 或 git status --short 简洁显示
  ```
  
* ??  M A
  
  ```tex
  ?? 新添加的未跟踪文件
  M 表示该文件被修改了但是还没放入暂存区
A 新添加到暂存区中的文件
  ```
  
* git add 可以用它开始跟踪新文件，或者把已跟踪的文件放到暂存区，还能用于合并时把有冲突的文件标记为已解决状态等

  ```
  git add <file> 将指定文件放入暂存区
  git add <directory> 将指定目录下所有变化的文件，放入暂存区
git add . 将当前目录下所有变化的文件，放入暂存区，等同于git add -A
  git add -u 表示只添加暂存区已有的文件（包括删除操作），但不添加新增的文件。
  git add -f <fileName> 表示强制添加某个文件，不管.gitignore是否包含了这个文件。
  ```
  

#### git commit 

```
用于将暂存区中的变化提交到仓库区。
git commit -m "message" message用于添加提交说明。
git commit <filename>  -m "message" 命令可以跳过暂存区，直接将文件从工作区提交到仓库区。先添加到暂存区，然后再将暂存区提交到仓库区。
git commit -am "message" 用于先将所有工作区的变动文件，提交到暂存区,再运行git commit
git commit -a 如果没有指定提交说明，运行下面的命令会直接打开默认的文本编辑器，让用户撰写提交说明。
git commit --allow-empty 用于没有提交信息的 commit。
git commit --amend - m "new commit message" 用于撤销上一次 commit，然后生成一个新的 commit。
git commit --fixup <commit> 当前添加的 commit 是以前某一个 commit 的修正。以后执行互动式的git rebase的时候，这两个 commit 将会合并成一个。
git commit --squash <commit> 参数的作用与--fixup类似，表示当前添加的 commit 应该与以前某一个 commit 合并成一个，以后执行互动式的git rebase的时候，这两个 commit 将会合并成一个。
```




