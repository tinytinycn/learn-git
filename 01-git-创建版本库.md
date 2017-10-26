创建版本库 repository
==
第一步
```
mkdir learngit
cd learngit
pwd //显示当前目录
```
第二步
```
git init //git跟踪当前目录进行管理
ls -ah //显示当前目录隐藏文件.git
```
**注意**
- 所有的版本控制系统只能跟踪 *文本文件* 的改动
- misicsoft word文件格式为二进制文件，无法跟踪
- 文本是有编码的，推荐使用 *UTF-8* 格式
- notepad++ 使用 *UTF-8 without DOM* 格式

添加文件到版本库
--
第一步
```
git add readme.md //把文件添加到仓库
```
第二步
```
git commit -m "commit a md file." //把文件提交到仓库
```

总结
--
- git init
- git add <file> **//可以多次使用，可以添加多个文件**
- git commit -m "describle content"
