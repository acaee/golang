# 函数

## 函数类型

- 普通函数
- 匿名函数
- 方法

## 函数定义

```go
//普通函数的定义，形参和返回值可省略
func 函数名(形参) 返回值 {

}
```

```go
//匿名函数的定义，形参和返回值可省略
a := func(形参) 返回值 {

}
```

```go
//方法的定义，形参和返回值可省略，必须绑定一个结构体
func (结构体) 方法名(形参) 返回值 {

}
```

## 传递变长参数

```go
//三个.代表函数需要传入多个int型字段
func GetStr(...int)  {
	
}
```

## `defer`

```go
package main

import "fmt"

func main() {
	//defer将语句压入栈中，在所有代码和return之间执行
	defer fmt.Println("5")
	fmt.Println("1")
	fmt.Println("2")
	fmt.Println("3")
	fmt.Println("4")
}
```

## 内置函数

> Go 语言拥有一些不需要进行导入操作就可以使用的内置函数。它们有时可以针对不同的类型进行操作，例如：len、cap 和 append，或必须用于系统级的操作，例如：panic。因此，它们需要直接获得编译器的支持。
>

| 名称                | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| close               | 用于管道通信                                                 |
| len、cap            | len 用于返回某个类型的长度或数量（字符串、数组、切片、map 和管道）；cap 是容量的意思，用于返回某个类型的最大容量（只能用于切片和 map） |
| new、make           | new 和 make 均是用于分配内存：new 用于值类型和用户定义的类型，如自定义结构，make 用于内置引用类型（切片、map 和管道）。它们的用法就像是函数，但是将类型作为参数：new (type)、make (type)。new (T) 分配类型 T 的零值并返回其地址，也就是指向类型 T 的指针。它也可以被用于基本类型：v := new(int)。make (T) 返回类型 T 的初始化之后的值，因此它比 new 进行更多的工作 |
| copy、append        | 用于复制和连接切片                                           |
| panic、recover      | 两者均用于错误处理机制                                       |
| print、println      | 底层打印函数，在部署环境中建议使用 fmt 包                    |
| complex、real、imag | 用于创建和操作复数                                           |

## 递归函数

```go
func recursion() {
   recursion()  //函数调用自身
}

func main() {
   recursion()
}
```

## 将函数作为参数

```go
package main

import (
    "fmt"
)

func main() {
    callback(1, Add)
}

func Add(a, b int) {
    fmt.Printf("The sum of %d and %d is: %d\n", a, b, a+b)
}

func callback(y int, f func(int, int)) {
    f(y, 2) // this becomes Add(1, 2)
}
```

## 闭包

```go
package main

import "fmt"

func main() {

	a := Add()
	fmt.Println(a(1))
}

func Add() func(int) int {
	sum := 0
	return func(i int) int {
		sum += i
		return sum
	}
}
```

