git02
==

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
