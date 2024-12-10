# 完整操作记录

## 数据库

### 登录创建movie数据库

![image-20241208215256535](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241208215256535.png)

### 创建表

![image-20241208215640109](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241208215640109.png)

### 导入数据

禁用外键约束：

```mysql
SET foreign_key_checks = 0;
```

执行脚本文件：

![image-20241208220212277](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241208220212277.png)

启用外键约束：

```mysql
SET foreign_key_checks = 1;
```



## 系统登陆界面

![image-20241208220629936](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241208220629936.png)

启用外键约束：

```mysql
SET foreign_key_checks = 1;
```

## 输入账号和密码之后，进入电影管理系统

![image-20241208220702622](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241208220702622.png)

## 点击每一个页面，结果如图所示

### 电影

![image-20241209150938224](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209150938224.png)

### 排行榜

![image-20241209105138958](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209105138958.png)

### 导演

![image-20241208221025451](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241208221025451.png)

### 演员

![image-20241209105110635](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209105110635.png)

## **下面测试每个表的增加、删除、查找、更新功能，以演员管理表为例，其他的表类似，只是属性不同**

### 增加

添加前演员个数为6085

![image-20241209151354300](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209151354300.png)点击右上角的添加演员，跳转到以下页面，填入对应信息：

![image-20241209151541434](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209151541434.png)

点击提交后，显示添加信息成功：

![image-20241209151923052](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209151923052.png)

点击确定跳转到演员表，发现表的末尾增加的添加的内容：

![image-20241209152021563](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209152021563.png)

### 删除

点击右侧的删除按钮，显示删除信息成功：

![image-20241209152105654](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209152105654.png)

跳转回演员表后看不到刚才添加的内容：

![image-20241209152201419](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209152201419.png)

### 修改

点击右侧操作列表中修改演员信息跳转到以下页面，填入修改信息后点击更新：

![image-20241209152357092](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209152357092.png)

显示修改成功，点击确认：

![image-20241209152338804](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209152338804.png)

跳转会演员列表后发现，1号演员的信息已经变成了修改后的内容：

![image-20241209152513331](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209152513331.png)

### 查询

在左侧窗口栏中随便选择一个要查询的属性，这里以电影ID为例：

![image-20241209152621431](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209152621431.png)

输入查询的值，点击搜索：

![image-20241209153051928](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209153051928.png)

出现所有电影ID符合查询值得内容：

![image-20241209152950959](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209152950959.png)

### 高级检索

![image-20241209193310743](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209193310743.png)

在电影表中，有一个高级查询功能，根据需要在查询框中输入，比如我们现在需要查询片名中含'Hack'的历史电影，输入后点击搜索：

![image-20241209170753375](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209170753375.png)

查询结果如下：

![image-20241209193032480](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209193032480.png)

## 设计至少一种统计表（有行列条件组成的一个二维表格），将统计结果输出到csv 或者 excel 文件，在高级检索中，有一个下载按钮如下，可以下载输出csv文件，得到查询结果

### 统计历史类电影

在类型区域选中历史：

![image-20241209193453201](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209193453201.png)

点击搜索得到查询结果：

![image-20241209193517128](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209193517128.png)

滑动到表格底端，点击下载CSV，可以下载成csv文件：

![image-20241209193540996](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209193540996.png)

![image-20241209193613158](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209193613158.png)

查看下载得到的文件：

![image-20241209193712974](C:\Users\kaka\AppData\Roaming\Typora\typora-user-images\image-20241209193712974.png)

**系统所有的功能测试如上，所有功能运行正常。**