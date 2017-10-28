分支管理
==
branch, 平行宇宙

创建和合并分支
--
```
// 创建 dev分支 并切换到dev分支
git checkout -b dev
// -b参数表示创建并切换, 效果等同下面
git branch dev
git checkout dev
// 查看 当前分支
git branch
// * 标记表示当前分支
// 在dev 分支修改内容, 切回master 分支
git checkout master
// 合并 dev分支到 master分支
git merge dev
// 合并成功, 可以删除dev分支
```
流程图大致如下

![master](https://www.liaoxuefeng.com/files/attachments/0013849087937492135fbf4bbd24dfcbc18349a8a59d36d000/0)

![checkout dev](https://www.liaoxuefeng.com/files/attachments/001384908811773187a597e2d844eefb11f5cf5d56135ca000/0)

![diff](https://www.liaoxuefeng.com/files/attachments/0013849088235627813efe7649b4f008900e5365bb72323000/0)

![merge dev](https://www.liaoxuefeng.com/files/attachments/00138490883510324231a837e5d4aee844d3e4692ba50f5000/0)

![delete dev](https://www.liaoxuefeng.com/files/attachments/001384908867187c83ca970bf0f46efa19badad99c40235000/0)

小结
--
- 查看分支 git branch
- 创建分支 git branch BRANCH_NAME
- 切换分支 git checkout BRANCH_NAME
- 创建并切换 git checkout -b BRANCH_NAME
- 合并某个分支到当前分支 git merge BRANCH_NAME
- 删除分支 git branch -d BRANCH_NAME
___________
解决冲突
--
```
//创建新分支feature1 ,修改内容并提交
git checkout -b feature1
git add *.md
git commit -m "add XXX"
//切回 master分支, 修改内容并提交
git checkout master
git add *.md
git commit -m "add YYY"
//合并 分支feature1到master, 发生冲突
git merge feature1
//根据提示, 解决冲突后提交
git add *.md
git commit -m "fix conflicts"
//删除分支feature1
git branch -d feature1
//查看分支合并情况
git log --graph --pretty=oneline --abbrev-commit
```
![conflicts](https://www.liaoxuefeng.com/files/attachments/001384909115478645b93e2b5ae4dc78da049a0d1704a41000/0)

小结
--
- 当git无法自动合并分支时, 就必须解决冲突. 解决冲突后, 提交, 合并完成.
- git log --graph 查看分支合并图

分支管理策略
--
通常，合并分支时，如果可能，Git会用Fast forward模式，但这种模式下，删除分支后，会 **丢掉** 分支信息。如果要强制禁用Fast forward模式，Git就会在merge时生成一个新的commit，这样，从分支历史上就可以 **看出分支信息** .

```
git checkout -b dev
//修改内容, 并提交
git add readme.md
git commit -m "add merge"
//切回master
git checkout master
//合并 dev分支到master分支
git merge --no-ff -m "merge with no-ff" dev
//本次合并创建一个commit
//查看历史日志
git log --graph --pretty=oneline --abbrev-commit
```
不使用fast forward模式, 如图
![no-ff](https://www.liaoxuefeng.com/files/attachments/001384909222841acf964ec9e6a4629a35a7a30588281bb000/0)

实际开发中的分支策略, 如图
![xx](https://www.liaoxuefeng.com/files/attachments/001384909239390d355eb07d9d64305b6322aaf4edac1e3000/0)

小结
--
- 合并分支时，加上 **--no-ff** 参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并.
