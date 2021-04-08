# 第三章 流程控制&循环

## if-else 结构

```go
if condition1 {
    // do something 
} else if condition2 {
    // do something else    
} else {
    // catch-all or default
}
```

## switch结构

```go
package main

import "fmt"

func main() {
    var num1 int = 7

    switch {
        case num1 < 0:
            fmt.Println("Number is negative")
        case num1 > 0 && num1 < 10:
            fmt.Println("Number is between 0 and 10")
        default:
            fmt.Println("Number is 10 or greater")
    }
}
```

## for循环

```go
for i := 0; i < 5; i++ {
    fmt.Printf("This is the %d iteration\n", i)
}
```

```go
for i, i2 := range collection {

}
```

```go
for true {

}
```

## break & continue & fallthrough & return

* `break`跳出当前循环
* `continue`结束本次循环，并开始一轮新的循环
* `fallthrough`穿透，在`switch`使用
* `return`结束当前方法

