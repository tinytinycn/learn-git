时光穿梭机
--
```
git status //查看仓库当前状态
git diff //查看difference
```
版本回退
--
```
git log //查看提交历史日志，由近到远
git log --pretty=oneline //简化输出信息
```
- 输出信息中包含了 SHA1计算出的十六进制表示的 commit id (版本号)
- **HEAD** 表示当前版本，**HEAD^** 表示上一个版本，**HEAD^^** 表示上上一个版本，**HEAD~100** 表示往上100个版本
```
git reset --hard HEAD^ //回退到上一个版本

git reset --hard e6d4501 //回退到某一个版本
git reflog //查看命令历史日志
```
小结
--
- git reset --hard commit_id
- git log
- git reflog
________________
工作区
--
可见目录文件夹就是一个工作区 working directory

版本库
--
工作区 有一个隐藏目录文件夹.git 就是git的版本库 respository
版本库 存在很多东西，比如stage暂缓区、git自动创建的一个分支master、指向master的一个指针HEAD

![respository](https://www.liaoxuefeng.com/files/attachments/001384907702917346729e9afbf4127b6dfbae9207af016000/0)

小结
--
- git add 把文件修改添加到暂缓区
- git commit 把暂缓区的所有内容提交到当前分支
________________
管理修改
--

git管理的是修改,并非文件

第一步 修改文件
```
git add readme.md
git status
cat readme.md //查看文档内容
```
第二部 再次修改文件
```
git commit -m "add new modified."
git status
```
第一次的修改被添加到暂存区,第二次的修改没有放入暂存区,git commit只负责把暂存区的内容提交到分支中
```
git diff HEAD --readme.md //查看工作区和版本库中最新版本的区别
```

小结
--
- cat <file>
- git diff HEAD - - \<file>
- git add 操作只是将修改的文件加入到暂缓区,如果不 add, 就不会被 commit到分支中
________________
撤销修改
--
第一步 修改文件, 未add

第二步 手动修改内容,可以恢复文件到到上一个版本

或者 第二步 可以丢弃工作区的修改
```
git checkout -- readme.md
```
执行该操作时存在两种情况:
1. 当自修改内容后, 还没有放入暂存区中, 撤销修改, 回到与版本库一样的状态
2. 当修改内容后, 且已经放入暂存区中, 而后又自修改, 撤销修改, 回到最近一次放入暂存区后的状态

接下来是上面第二种情况的撤销:
```
git add readme.md
git status
git reset HEAD readme.md //把暂存区的修改撤销掉unstage, 放回工作区
git checkout -- readme.md //接着丢弃工作区的修改
```

还有一种情况, 将修改后的文件提交到分支, 就只能回退到上个版本了

小结
--
- git check - - \<file> 总是回到最近一次的commit 或 add 之后的状态
- **情况一:** 修改了工作区的内容, 想直接丢弃工作区的修改, 直接执行命令
- **情况二:** 修改了工作区的内容, 已经放入暂存区, 想丢弃修改, 执行git reset HEAD file, 回到情况一
- **情况三:** 提交了暂缓区修改到版本库, 想撤销本次提交, 只能版本回退(暂时未考虑推送到远程库)
________________
删除文件
--

git中, 删除也是一个修改操作

工作区删除操作:
```
rm readmd.md //直接删除文件
git status //此时,工作区与版本库不一致,
```
版本库删除操作:
```
rm readme.md
git status
git rm readme.md //此时,工作区与版本库都删除了文件
git commit
```

两种情况:
1. 如果确实需要删除版本库中的文件, 执行 git rm 命令删除并 git commit 提交操作
2. 如果误删除了工作区的文件, 执行 git checkout -- file, 撤销删除操作, 回到最近版本

小结
--
- git rm 用于删除一个文件, 如果文件已经被提交到版本库中, 不用担心在工作区误删除了.
________________
over
