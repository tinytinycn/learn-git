# cherry-pick

对于多分支的代码库，将代码从一个分支转移到另一个分支是常见需求。

临时将dev分支上某个或某几个commit提交合并到主分支上
```git
git cherry-pick <commitHash>
git cherry-pick <HashA> <HashB>
```

```text
// check-pick f 之前
a - b - c - d   Master
     \
       e - f - g Feature

// cherry-pick f 之后           
a - b - c - d - f   Master
         \
           e - f - g Feature    
```

如果操作过程中发生代码冲突，Cherry pick 会停下来，让用户决定如何继续操作。

1. --continue

用户解决代码冲突后，第一步将修改的文件重新加入暂存区（git add .），第二步使用下面的命令，让 Cherry pick 过程继续执行。

`git cherry-pick --continue`

2. --abort

发生代码冲突后，放弃合并，回到操作前的样子。

3. --quit

发生代码冲突后，退出 Cherry pick，但是不回到操作前的样子。