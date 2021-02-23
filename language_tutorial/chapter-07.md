# 接口与反射

## 接口与实现

```go
package main

import "fmt"

func main() {
	var mouse Mouse
	var computer Computer
	computer.Working(mouse)
}

type Computer struct {

}

func (c Computer) Working(usb USB)  {
	usb.Start()
	usb.Stop()
}

type USB interface {
	Start()
	Stop()
}

type Mouse struct {

}

func (m Mouse) Start()  {
	fmt.Println("鼠标开始工作")
}

func (m Mouse) Stop()  {
	fmt.Println("鼠标结束工作")
}
type Keyboard struct {

}

func (k Keyboard) Start()  {
	fmt.Println("键盘开始工作")
}

func (k Keyboard) Stop()  {
	fmt.Println("键盘结束工作")
}
```

## 对象与继承

```go

import "fmt"

func main() {

	var person Person

	person.Say()

}

type Person struct {
	age string
	name string
	sex bool
}

func (p Person) Say()  {
	fmt.Println("我是人")
}

type Doctor struct {
	Person
}
```

## `type-switch`

```go
func main() {

	var x = 10
	var y interface{} = x

	switch i := y.(type) {
	case string:
		fmt.Println("字符串类型:",i)
	case int:

		fmt.Println("i的类型为int类型,值为:",i)
	}

}
```

## 反射

>在计算机科学中，反射是指计算机程序在运行时（Runtime）可以访问、检测和修改它本身状态或行为的一种能力。用比喻来说，反射就是程序在运行的时候能够“观察”并且修改自己的行为。

```
//获取包名
//获取结构体名
//获取属性并修改
//获取方法并调用
```

