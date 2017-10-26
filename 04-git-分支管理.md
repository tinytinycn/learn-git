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
小结
--
- 当git无法自动合并分支时, 就必须解决冲突. 解决冲突后, 提交, 合并完成.
- git log --graph 查看分支合并图
