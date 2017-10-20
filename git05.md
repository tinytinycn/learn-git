git05
==

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