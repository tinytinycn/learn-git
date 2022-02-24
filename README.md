# Git 日常命令

1. 创建仓库 & 添加文件
```git
cd /your/project/path
git init
touch new-add-file.md
git add .
git commit -m "add new file"
```

2. 编辑 & 提交
```git
vi new-add-file.md
git add new-add-file.md
git commit -m "modified file"
git status
git log //查看历史commit提交
```

3. 历史提交 & 版本回滚
```git
git log //查看提交历史日志，由近到远
git log --pretty=oneline //简化输出信息
git reset --hard HEAD^ //回退到上一个版本
git reset --hard e6d4501 //回退到某一个版本
```

4. 克隆远程仓库
```git
git clone git@github.com:tinytinycn/learn-git.git
```

5. 为本地仓库添加一个远程仓库
```git
git remote add origin git@github.com:tinytinycn/learn-git.git
// 第一次 推送本地 master 分支到 远程origin 分支时， 加上 -u 参数
git push -u origin master
// 后续推送简化命令
vi new-add-file.md
git add .
git commit -m "modified file"
git push origin master
```

6. 创建并切换分支
```git
git branch // 当前在master分支
git checkout -b dev

// 等价操作
git branch dev
git checkout dev
```

7. 合并分支代码

通常 fast-forward 快速合并后，你会删除掉 dev 分支，因此会丢失分支信息
```git
git branch // 当前在dev 分支，进行了操作，并commit提交之后
git checkout master
git merge dev // 将dev 分支代码合并到master 分支
git branch -d dev // 合并结束，可以狠心删除 dev 分支
```

禁用 fast-forward 模式的合并
```git
git merge --no-ff -m "merge with no-ff" dev
git log --graph --pretty=oneline --abbrev-commit
```

![no-ff-merge](img/no-ff-merge.png)

8. 修复紧急缺陷BUG分支操作
修复bug分支统一命名：fixBug-bug版本，例如 fixbug-v4.1.1
```git
//从master 分支下，克隆来有bug的分支，在fixbug分支下去修复它，修复好了，再合并到master分支和develop分支，删除该bug分支。
git checkout -b fixBug-bug版本 master
//一顿操作，修复缺陷后
git checkout master
git merge --no-ff fixBug-bug版本
git checkout develop
git merge --no-ff fixBug-bug版本
//确认无误后，删除该bug分支
git branch -d fixBug-bug版本
```

