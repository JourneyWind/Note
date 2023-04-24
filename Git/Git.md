# Git

配置

打开Git Bash

| git config --global user.name 用户名 | 设置用户签名（用户名） |
| ------------------------------------ | ---------------------- |
| git config --global user.email 邮箱  | 设置用户签名（邮箱）   |

查看

git config --global --list

> 注意：如果用了 `--global` 选项，那么更改的配置文件就是位于当前计算机用户主目录下的那个 `.gitconfig` 文件，以后所有的项目都会默认使用这里配置的用户信息；如果要在某个特定的项目中使用其他名字或者邮箱，只要去掉 `--global` 选项重新配置即可，新的设定保存在当前项目的 .git/config 文件里

## 其余命令

| `git init`                                                   | 初始化本地库                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `git status`                                                 | 查看本地库状态                                               |
| `git add 文件名`                                             | 添加到暂存区<br />（`git add .` 添加所有）                   |
| `git rm --cached 文件名`                                     | 搁置/移除暂存区文件<br />`git rm --cached *` 搁置所有        |
| `git commit -m "日志信息" 文件名`                            | 提交到本地库<br />（不加文件名表示提交所有）                 |
| `git commit --amend`                                         | 修改提交日志信息                                             |
| `git reflog`                                                 | 显示所有的操作记录，包括提交，回退的操作                     |
| `git log`                                                    | 显示所有提交过的版本信息，不包括已经被删除的 commit 记录和 reset 的操作 |
| 注意：git reflog 常用于恢复本地的错误操作；<br />场景：我们 `commit` 了一个操作，发现提交的是错误的，于是我们进行了回退，`git reset --hard HEAD^`，就是把工作区的文件也回退还原了，这时候突然发现之前的提前是正确的，想再回退到回退之前的，便去找到之前的版本号进行回退，使用 `git log` 发现之前提交的版本号记录根本不存在了，这时只能使用 `git reflog` |                                                              |
| `git reset --hard 版本号`                                    | 版本穿梭（硬撤销）                                           |
| `git reset --soft 版本号`                                    | 版本穿梭（软撤销）                                           |
| 注意：<br />- 硬撤销：本地代码会直接变更为指定的提交版本，**慎用**！删除工作空间改动代码，撤销 commit，撤销 git add .，注意完成这个操作后，就恢复到了上一次 commit 后的状态<br />- 软撤销：本地代码不会变化，只是 git 转改会恢复为 commit 之前的状态，不删除工作空间改动代码，撤销 commit，不撤销 git add .<br />`git reset --soft HEAD^`：一大用途，撤销 commit，但不撤销 add . |                                                              |
| `git branch 分支名`                                          | 创建分支                                                     |
| `git branch -v`                                              | 查看分支                                                     |
| `git checkout 分支名`                                        | 切换分支                                                     |
| `git merge 分支名`                                           | 把指定的分支合并到当前分支上（可能发生合并冲突，便需要人工解决） |
| `git remote -v`                                              | 查看当前所有远程地址别名                                     |
| `git remote add 别名 远程地址`                               | 为远程地址起别名                                             |
| `git remote rm 别名 `                                        | 删除远程仓库别名                                             |
| `git push 别名 分支`                                         | 推送本地分支上的内容到远程仓库                               |
| `git clone 远程地址`                                         | 将远程仓库的内容克隆到本地                                   |
| `git pull 远程库地址别名 远程分支名`                         | 将远程仓库对于分支最新内容拉取下来后与当前本地分支直接合并（可能发生合并冲突，便需要人工解决） |

## 案例流程

![01](Git.assets/01.png)

![02](Git.assets/02.png)

![03](Git.assets/03.png)

![04](Git.assets/04.png)

![05](Git.assets/05.png)

![06](Git.assets/06.png)

![07](Git.assets/07.png)

![08](Git.assets/08.png)

![09](Git.assets/09.png)

![10](Git.assets/10.png)

![11](Git.assets/11.png)

![12](Git.assets/12.png)

![13](Git.assets/13.png)

![14](Git.assets/14.png)

![15](Git.assets/15.png)

![16](Git.assets/16.png)

![17](Git.assets/17.png)

![18](Git.assets/18.png)

![19](Git.assets/19.png)

![20](Git.assets/20.png)

![21](Git.assets/21.png)

![22](Git.assets/22.png)

![23](Git.assets/23.png)

![24](Git.assets/24.png)

![25](Git.assets/25.png)

![26](Git.assets/26.png)

![27](Git.assets/27.png)

![28](Git.assets/28.png)

![29](Git.assets/29.png)

![30](Git.assets/30.png)

![31](Git.assets/31.png)

![32](Git.assets/32.png)

![33](Git.assets/33.png)

![34](Git.assets/34.png)

![35](Git.assets/35.png)

## 一般流程

### 初始化仓库

````
git init
````

### 添加到暂存区

````
git add 文件名
````

### 提交到本地库

````
git commit -m "日志信息" 文件名
````

### 为远程地址起别名

````
git remote add 别名 远程地址
````

`git remote -v`  查看当前所有远程地址别名

### 推送本地分支上的内容到远程仓库

````
git push 别名 分支
````

## SSH

ls -la ~./ssh

![image-20230424204616217](Git.assets/image-20230424204616217.png)

如果看到以下输出，那么说明已经有 ssh 密钥（以 .pub 结尾的文件）

### 生成新的 ssh 密钥

```bash
ssh-keygen -t rsa -C "your_email@example.com"
```

### 查看ssh是否正常运行

````
$ eval
$ ssh-agent -s
````

![image-20230424204851279](Git.assets/image-20230424204851279.png)

## 测试 ssh 连接

````
ssh -T git@github.com
````

![image-20230424205013622](Git.assets/image-20230424205013622.png)

看到github 用户名，说明成功



