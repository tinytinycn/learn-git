远程仓库
==
git是分布式版本控制库, 同一个git仓库可以分不到不同的机器上.

github是一个git仓库托管服务. 需要一个github账号, 可以获得git远程仓库.

本地仓库和github远程仓库之间的传输, 是通过ssh加密的.

配置
---
```
//第一步创建SSH key, 打开shell输入命令
ssh-keygen -t rsa -C "tinytiny.cn@gmail.com"
//执行成功, 用户主目录.ssh目录里有 id_rsa和 id_rsa.pub两个文件.两个是秘钥对, id_rsa私钥,不能泄露. id_rsa.pub公钥,放心别人使用.

//第二步添加SSH key, 打开github
Account settings>>ssh keys>>Add SSH Key>>填title>>粘贴id_rsa.pub文件内容>>Add Key
//可以添加多个key.
```
________________
添加远程库
==
已经创建了一个本地库, 现在需要创建一个远程库,并且在这两个仓库之间进行同步.github仓库既可以作为备份, 也可以同其他人协同工作.

步骤
--
```
//创建一个空的远程库
登陆github >> 右上角 Create a New Repo >> 填入Repository Name >> 其他默认设置 >> Create Repository

//本地关联到远程库, 本地库打开shell
git remote add origin git@github.com:tinytinycn/learngit.git
//本地库推送到远程库, 当前分支master推送到远程
//第一次使用 -u 参数, 推送并关联
git push -u origin master
//以后推送使用简化命令
git push origin master
```
________________
从远程库克隆
==
开发时, 一般先创建一个远程库, 而后从远程库克隆.

步骤
--
```
1. 创建一个新的远程库repository, 勾选Initiablize this repository with a README. github自动创建一个readme.md文件.
2. git clone 克隆远程库
git clone git@github.com:tinytinycn/learngit.git
cd learngit //进入目录文件夹
ls  //查看文件
```
________________
over
