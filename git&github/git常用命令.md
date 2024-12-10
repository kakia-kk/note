# git常见操作

## 创建仓库

### 🌏初始化仓库

```bash
git init
```

主要用来初始化一个空的git本地仓库。执行完上面的命令，当前目录下会自动生成.git隐藏文件夹，该隐藏文件夹就是git版本库

### 🌏查看仓库状态

```bash
git status
```

🌏设置用户信息

```bash
git config --global user.name 'your_name ' 

git config --global user.email 'your_email@qq.com'
```

🌏创建钥匙

```bash
ssh-keygen -t rsa -C “email”
```

### 🌏验证钥匙

```bash
ssh -T git@github.com
```

### 🌏与远程仓库建立连接

```bash
git remote add origin yourAddress
```

例如：

```bash
git remote add origin git@github.com:yourName/repositoryname.git
```

### 🌏重新设置仓库url地址

```bash
git remote set-url origin 地址
```

例如： 

```bash
git remote set-url origin https://github.com/yourname/learngit.git (这个是你的复制的仓库地址)
```


🌏初次拉取代码到本地

```bash
git pull origin master --allow-unrelated-histories
```

🌏克隆仓库代码到本地

```bash
git clone 远程地址
```

例如：

```bash
git clone git@github.com:FX336494/admin_v1.git
```

### 🌏拉取分支代码

```bash
git pull origin '分支名 ’
```

例如：

```bash
git pull origin  'dev'
```



## 提交文件到仓库

### 🌏添加文件

添加文件到缓存区

```bash
git add ‘文件名’
```

### 🌏添加所有文件

点表示所有文件到缓存区

```bash
git add .
```

### 🌏重命名文件名称

git mv 旧文件名 新文件名，如将`old.html`文件修改为`new.html`: 

```bash
git mv old.html new.html
```



## 提交指定文件

### 🌏git add 文件名称

cd命令进入到文件所在的目录 或在文件管理器中找到文件右键 Git Bash Here
如：提交index.vue: git add index.vue 然后commit与 push

## 提交指定文件夹中的所有文件

cd命令进入到所要提交的文件夹或在文件管理器中右键 Git Bash Here

git add .
然后 commit 与 push

### 🌏提交文件

git commit -m ‘备注’

如：

```bash
git commit -m '首次上传'
```



### 🌏推送文件到仓库

```bash
git push origin master
```

推送文件到仓库master（主）分支

主要是将暂存区里的改动给提交到本地的版本库。每次使用git commit 命令我们都会在本地版本库生成一个40位的哈希值，这个哈希值也叫commit-id，commit-id在版本回退的时候是非常有用的，它相当于一个快照,可以在未来的任何时候通过与git reset的组合命令回到这里。


### 🌏强制推送到分支

```bash
git push -u -f origin master
```

 提交到远程仓库，这个命令中的 -f 是强制推送，因为远程仓库只有初始化的文件，所以强制推送上去就行了，
 不加-f 会报当前分支没有远程分支，强制推送可以覆盖master，这样就完成了第一次提交的步骤)

## 删除仓库文件

### 🌏查看目录

```bash
dir
```



### 🌏删除指定文件

git rm 文件名

如: 

```bash
git rm index.html
```



### 🌏返回到上一个版本代码

```bash
git reset --hard HEAD^
```



### 🌏返回到上两个版本代码

```bash
git reset --hard HEAD^^
```



### 🌏返回到上三个版本代码

```bash
git reset --hard HEAD^^^
```



### 🌏查看不同版本的 id

```bash
git log --pretty=oneline
```



### 🌏返回到指定版本代码

```bash
git reset --hard 具体版本号
```

注意是将**本地文件返**回到指定版本
如:git reset --hard 8ab7b23b2b305f9b793ed95a06c1add1d0a5cd61
然后 git push -f -u origin master 将代码推送到仓库 

## 分支操作

### 🌏查看有哪些分支

```bash
git branch
```

### 🌏创建分支

```bash
git branch 分支名
```

### 🌏切换分支

```bash
git checkout 分支名
```

### 🌏创建和切换同时进行

```bash
git checkout -b 分支名
```

### 🌏删除本地分支a

```bash
git branch -d a
```

### 🌏强制删除本地分支a

```bash
git branch -D a
```

### 🌏删除远程分支

```bash
git push origin --delete 分支名
```



### 🌏合并分支

将dev分支合并到master分支

```bash
git checkout master //先切换到master分支
git pull up master //拉取代码
git merge dev //合并代码
git push origin master //推送到master分支

```

## 查看已链接仓库信息

```bash
git remote	//它会列出每个远程库的简短名字。

git remote -v	//它会列出远程库的详细信息
```



## 恢复本地删除的文件

在本地项目中右键误删文件，想再pull回来,提示`Already up-to-date`

### 方法1：

```bash
git fetch --all
git reset --hard origin/master(master可修改为对应分支名)
git pull
```



### 方法2：

恢复单个文件 

```bash
git checkout index.vue git checkout 文件名
```

恢复当前目录

```bash
 git checkout .
```

或者

```bash
git checkout 分支名 --index.uve完整相对路径
```

git fetch是将远程主机的最新内容拉到本地，用户在检查了以后决定是否合并到工作本机分支中。
而git pull 则是将远程主机的最新内容拉下来后直接合并，即：git pull = git fetch + git merge，
这样可能会产生冲突，需要手动解决。

github提交注释规范

```bash
git commit -m “提交类型+代码修改描述”
```

提交类型：
feat: 修改/增加新功能
fix: 修改bug/功能代码的变更
docs: 文档相关变更
style: 不影响代码含义的变更(空白/格式/缺少符号等)
refactor: 代码重构变更
perf: 改进性能的变更
test: 添加/修改现有的测试
chore: Build/.gitignore/辅助工具/库(文档生成)等变更
Example: feat:修改侧边栏默认状态

## 常见错误

### git pull

error: You have not concluded your merge (MERGE_HEAD exists).
hint: Please, commit your changes before merging.
fatal: Exiting because of unfinished merge.

错误：您尚未结束合并（合并头存在）。
提示：请在合并之前提交更改。
致命：因未完成的合并而退出。

#### 方法1 : 保留本地更改

```bash
git merge --abort
git reset --merge
```

然后commit 提交本地修改

```bash
git pull
```

#### 方法2 : 放弃本地修改

```bash
git fetch --all
git reset --hard origin/master
git fetch
```

```bash
error: Your local changes to the following files would be overwritten by merge:
        xxx.vue
        xxx.ts
Please commit your changes or stash them before you merge.
```

git stash // 暂存到堆栈区
git stash list // 查看stash内容
git pull // 拉取代码
git stash pop // 应用到本地分支
打开冲突文件，选择采用 ‘本地/线上/全部’ 代码

