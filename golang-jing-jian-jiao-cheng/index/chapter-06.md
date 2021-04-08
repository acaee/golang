# 第七章 结构体（struct）与方法（method）

## 结构体\(`struct`\)的定义

```text
type 名称 struct {
    字段名 字段类型
}
```

## 创建结构体实例

```go
type File struct {
    fd int
    name string
}

func NewFile(fd int, name string) *File {
    if fd < 0 {
        return nil
    }
    return &File{fd, name}
}

f := NewFile(10, "./test.txt")
```

## 带标签的结构体

```go
package main

import (
    "fmt"
    "reflect"
)
func main() {

    stu := Student{
        ID:   1,
        Name: "张三",
        Age:  19,
    }
    stuType := reflect.TypeOf(stu)
    fmt.Println(stuType)
    field := stuType.Field(0)
    fmt.Println(field.Tag)
}
type Student struct {
    ID int `id`
    Name string `name`
    Age int `age`
}
```

## 匿名字段和内嵌结构体

```go
package main

import "fmt"

type innerS struct {
    in1 int
    in2 int
}

type outerS struct {
    b    int
    c    float32
    int
    innerS
}

func main() {
    outer := new(outerS)
    outer.b = 6
    outer.c = 7.5
    outer.int = 60
    outer.in1 = 5
    outer.in2 = 10

    fmt.Printf("outer.b is: %d\n", outer.b)
    fmt.Printf("outer.c is: %f\n", outer.c)
    fmt.Printf("outer.int is: %d\n", outer.int)
    fmt.Printf("outer.in1 is: %d\n", outer.in1)
    fmt.Printf("outer.in2 is: %d\n", outer.in2)

    outer2 := outerS{6, 7.5, 60, innerS{5, 10}}
    fmt.Println("outer2 is:", outer2)
}
```

## 内嵌结构体

```go
package main

import "fmt"

type A struct {
    ax, ay int
}

type B struct {
    A
    bx, by float32
}

func main() {
    b := B{A{1, 2}, 3.0, 4.0}
    fmt.Println(b.ax, b.ay, b.bx, b.by)
    fmt.Println(b.A)
}
```

## 方法

```go
package main

import "fmt"

func main() {

    var stu Student
    stu.Say()

}

type Student struct {
    ID int
    Name string
    Age int
}

func (s Student) Say()  {
    fmt.Println("我不上学了")
}
```

