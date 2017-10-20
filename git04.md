git04
==

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
