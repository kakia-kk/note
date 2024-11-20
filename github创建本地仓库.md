# github创建本地仓库

## config设置

### 设置username和email

```shell
$ git config --global user.name  "name"//自定义用户名
$ git config --global user.email "youxiang@qq.com"//用户邮箱
```

![image-20241120114256642](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241120114256642.png)

#### 设置username和email作用

主要是为了区分上传的人

### 查询

```shell
 git config --global user.name
 git config --global user.email
```

![image-20241120114546051](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241120114546051.png)

查询当前仓库的

```bash
 git config user.name
 git config user.email
```

![image-20241120114704815](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241120114704815.png)

## github与git连接

本地Git仓库和GitHub仓库之间的传输是**通过SSH加密传输的**，所以需要配置ssh key。

### 创建SSH Key

git bash创建ssh key（**引号内是github注册使用的邮箱!!**）

```bash
$ ssh-keygen -t rsa -C "3344850985@qq.com"
```

![image-20241120121653131](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241120121653131.png)

### 在用户的主目录下找到ssh key

用的是public

![image-20241120121926386](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241120121926386.png)

### 在github上添加ssh key

### 本地Git仓库

### 建本地的版本库

相当于新建一个文件夹

进入文件夹，右键-Git Bash

```bash
git init #初始化成一个Git可管理的仓库
```

![image-20241120111644040](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241120111644040.png)

输入之后可以观察到文件夹对应位置出现了一个.git的文件，它是Git用来跟踪和管理版本库的。如果你看不到，需要设置一下让隐藏文件可见。

```bash
git status #查看当前的状态
```

红色字表示未add到Git仓库上的文件

绿色字表示已add到Git仓库上的文件

```bash
git add . #把项目/源代码添加到仓库
```

```bash
git commit -m "first commit" #把项目提交到仓库，可以写上注释
```

### Github上建立仓库

登录github-my

### 关联远程仓库

![image-20241120113840394](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241120113840394.png)

```bash
git remote add origin https://github.com/kakia-kk/note.git
```



## 本地内容上传

```bash
git push -u origin master #由于新建的远程仓库是空的，所以要加上-u这个参数
```

```bash
git push origin master #之后仓库不是空的，就不用加上-u
```

![image-20241120122059053](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241120122059053.png)

因为我用的是外部硬盘，所以直接操作会报错如下：

![image-20241120115007442](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241120115007442.png)

```bash
git config --global --add safe.directory E:/note #将当前目录标记为安全的目录
```

![image-20241120115234947](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241120115234947.png)

可以看到输入之后出现了（master）

修改文件之后重新提交：

![image-20241120122329112](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241120122329112.png)