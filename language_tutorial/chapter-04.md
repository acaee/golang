# 数组与切片

## 数组的定义

```go
var 数组名 [长度]数组类型
var a [3]int
var a [3]int = [3]int{1,2,3}
var b = [3]int{1,2,3}
var c = [...]int{1,2,3}
var d = [...]int{1: 100,2:200,0:300}
f := [...]string{1:"tom", 0:"jack", 2:"tony"}
```


## 切片的定义

```go
var 切片名 []类型
var 切片名 []类型 = make([]类型, 长度, 容量)
var a []int
var b []int = make([]int,len)

```

## `len()`和`cap()`函数

```go
len() //获取长度
cap() //获取容量
```

`append()`和`copy()`函数

```go
//只能作用在切片上
1. append()
2. copy()
```

## 遍历数组

```go
// for i
// for range
```