git06
==

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
