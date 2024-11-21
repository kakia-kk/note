# go语言

## 用途

go搭载web服务器

？web服务器是什么：Web服务器一般指的是“网站服务器”，是某种驻留在因特网上的计算机程序，可以向请求终端提供服务，主要功能时存储、处理和传递网页给“客户”，传递内容一般是HTML文档、图像、样式表或脚本等，也可以放置网站文件以供浏览或下载。 目前主流的web服务器主要是**Apache、Nginx、IIS**，还有较多使用的Tomcat、Jetty、WebSphere，WebLogic，Kerstrel等。下图为市场占有率历史数据，Apache占有率较高，但是在前1K网站排名中，Nginx占有率最高。

go语言在高性能分布式系统领域有优势

## 基本知识

包声明:表示访问的文件属于哪个包同一个文件夹下只能有一个包名，但是包名和文件夹名没有必然关系

```go
package main #表示可以独立运行的程序
```

引入包：

```go
import packageName
```

标识符为大写字母的方法可以被外部使用（相当于别的语言里的public）方法调用：

```go
packageName.functionName
```

生成go.mod文件：

```shell
go mod init
```

