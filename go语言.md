# go语言

## 简介

Go（又称golang）是Google开发的一种静态强类型、编译型、并发型，并具有垃圾回收功能的编程语言。Go语言是近年开始活跃的一门编程语言，在保持简洁、快速、安全的情况下提供了对海量并发的支持，这也使其成为一门适合Web 服务器，存储集群或类似用途的编程语言。

## windows系统下载安装go语言环境

1. 下载安装包

2. 在终端输入go version查看go语言版本是否正确

3. 查看go env，确保GO111MODULE='on'GOPROXY='https://goproxy.cn,direct'

   若不是可以在终端输入：

   ```shell
   go env -w GOPROXY=https://goproxy.cn,direct
   go env -w GO111MODULE=on
   ```

## go mod使用

Go module 是Go1.11版本开始发布的依赖管理方案，从Go1.14版本开始推荐投入生产环境使用，上述配置环境go env中的GO111MODULE查看打开状态与之相关（Go1.16版本已默认打开）。

### 示例

在工作文件夹下打开命令行：

```shell
mkdir hello
cd hello 
// 初始化生成 go.mod 文件
go mod init hello 
-> go: creating new go.mod: module hello
```

随后在该目录下创建文件hello.go，并写入如下内容后保存：

```go
package main

import "fmt"

func main() {
fmt.Println("hello world!")
}
```

在命令行输入 go run hello.go得到hello world!输出后即为成功。

在这个例子中，‘go mod init hello’ ，其中的hello是当前目录下的go module名称，go module名称可以自定义，例如‘go mod init github/hello’或者‘go mod init world’。这个名称将决定了后续包引用时的前缀。在执行‘go mod init hello’命令后，go会生成一个依赖声明文件go.mod，内容如下。由于代码文件中仅引用了go语言系统fmt库，go.mod文件仅会显示module名与go版本。如果程序引用了外部的go 程序库，即第三方库，在go mod所在的目录下执行命令‘go mod tidy’ 或者‘go get 第三方库url’，会帮助你将引用库的路径以及对应版本号记录到这个文件，无需手动修改。

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

```go
1. //语言结构
2. package main //声明该 go 文件属于 main 包
3. import ( //导入包语法
4. "fmt" //包含格式化 I/O 函数，如 Printf,Scanf 等
5. "database/sql"
6. )
7.
8. func main(){ //"{"不能单独写在一行
9. ...
10. }
```

```go
1. //变量与常量
2. var a string = "hello" //声明 string 类型变量 a，并赋值“hello”；Go 语言
不以分号结尾。
3. b := "world" //将"world"赋值给变量 b，并自动判断类型；b 必须为新变
量。
4. var c bool //声明变量 c 并赋予“零值”。
5. const d uint32 = 1 //定义常量
```

```go
1. //控制语句（Go 不以缩进来区分代码层次）
2. //for 循环，初始化语句和后置语句都是非必须的。
3. sum := 0
4. for i := 0; i < 10; i++ {
5. sum += i
6. }
7.
8. //if...else 语句，if 语句可以在条件表达式前执行一个简单的语句。
9. if v := math.Pow(x, n); v < lim {
10. return v
11. } else {
12. fmt.Printf("%g >= %g\n", v, lim)
13. }
14.
15. //switch 语句，与其他语言的区别在于，case 可以不为常量；执行完匹配
case 后会自动停止（相当于加了 break）
16. fmt.Print("Go runs on ")
17. switch os := runtime.GOOS; os {
18. case "darwin":
19. fmt.Println("OS X.")
20. case "linux":
21. fmt.Println("Linux.")
22. default:
23. // freebsd, openbsd,
24. // plan9, windows...
25. fmt.Printf("%s.\n", os)
26. }
27.
28. //defer 语句，会将函数推迟到外层函数返回之后执行。如本例程将在 main
函数执行完输出 hello 后，再输出 world。
29. func main() {
30. defer fmt.Println("world")
31. fmt.Println("hello")
32. }
```

```go
1. //数据结构
2. //指针,与 C 语言类似
3. i := 10
4. p = &i
5. *p = 11
6.
7. //结构体
8. type LAB struct{
9. number int
10. date string
11. done bool
12. }
13. lab1 := LAB{1,"2020-10-01",false}
14.
15. //数组与切片
16. var balance = [5]float32{1000.0, 2.0, 3.4, 7.0, 50.0} //声明并赋值了
长度 5，类型 float32 的数组
17. var s []float = balance[1:4] //[]T 表示切片类型，其*引用*了数组
balance 的 1 至 3 号元素
18. s1 := []int{1,2,3} //也可直接创建一个切片
19.
20. //映射,元素为键值对
21. var m = map[string]int{
22. "store1" : 100
23. "store2" : 90
24. }
25. m["store1"] = 80 //修改元素
26. delete(m,"store1") //删除元素
27.
28. //函数值和闭包
29. //在 Go 语言中，函数可以作为值被传递，也可以作为其他函数的参数或返
回值。
30. //函数作为值被赋给 hypot，而 hypot 可作为参数被其他函数调用。
31. hypot := func(x, y float64) float64 {
32. return math.Sqrt(x*x + y*y)
33. }
34. fmt.Println(hypot(5, 12))
35. //go 函数可以是闭包，闭包是一个函数值，它引用了其函数体之外的变
量，该函数可以访问并赋予其引用的变量的值。
36. func adder() func(int) int {
37. sum := 0
38. return func(x int) int { //该闭包与其外部的 sum 相绑定
39. sum += x
40. return sum
41. }
42. }
43.
44. func main() {
45. pos = adder()
46. for i := 0; i < 10; i++ {
47. fmt.Println(pos(1)) //由于 pos 与 sum 绑定，每调用一次 pos(1)
都会执行 sum+1，并维持 sum 的值。
48. }
```

```go
1. //方法和接口
2. //Go 语言没有类，但是通过结构体和方法实现了相关功能。
3. type Vertex struct { //定义结构体，其成员相当于类的成员变量
4. X, Y float64
5. }
6.
7. func (v Vertex) Abs() float64 { //定义方法,(v Vertex)表示接收者，该方法类似
于类的成员方法
8. return math.Sqrt(v.X*v.X + v.Y*v.Y)
9. }
10.
11. //接口是对所有的具有共性的方法的一种抽象，任何其他类型只要实现了这
些方法就是实现了这个接口。
12. type Car interface { //所有汽车都能驾驶，因此抽象 drive()方法
13. drive()
14. }
15. type TeslaCar struct { //其他汽车类型，只要实现了 call()方法，
就是是实现了 Car 接口
16. }
17. func (tc TeslaCar) drive() {
18. fmt.Println("I am tesla!")
19. }
20. type BydCar struct {
21. }
22. func (bc BydCar) drive() {
23. fmt.Println("I am BYD!")
24. }
25. func main() {
26. var car Car
27. car = new(TeslaCar) //接口变量可以直接被赋值实现了该接口的类
型实例。
28. car.drive()
29. car = new(BydCar)
30. car.drive()
31. }
32.
33. //接口具有广泛的用处，例如 go 中的错误处理就是用接口实现的
34. type error interface {
35. Error() string
36. }
```

```go
1. //并发
2. //go 支持高并发的原因就在于其 goroutine，是一种轻量级线程，可用 go 关键字开
启。
3. go f(x,y,z) //创建一个 goroutine 并在内执行 f(x,y,z)函数
4. //由于 goroutine 之间是相互独立的，因此连续开启两个 goroutine 后，二者内部
运行是没有先后关系的。
5. //并发部分涉及内容较多，例如 goroutine 之间的通信，暂不在 Go 语言入门考虑内，感兴趣的可自行了解。
```

## 使用go语言构造区块链