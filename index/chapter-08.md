# 第九章 其他

## 错误处理

```go
func protect(g func()) {
    defer func() {
        log.Println("done")
        // Println executes normally even if there is a panic
        if err := recover(); err != nil {
        log.Printf("run time panic: %v", err)
        }
    }()
    log.Println("start")
    g() //   possible runtime-error
}
```

## 管道\(`chan`\)

### 管道\(`chan`\)的定义

```go
// 声明不带缓冲的通道
ch1 := make(chan string)
// 声明带10个缓冲的通道
ch2 := make(chan string, 10)
// 声明只读通道
ch3 := make(<-chan string)
// 声明只写通道
ch4 := make(chan<- string)
```

## 协程

```go
func main() {

    intChan := make(chan int,50)
    exitChan := make(chan bool,1)
    go Write(intChan)
    go Read(intChan,exitChan)

    for {
        _, ok := <- exitChan
        if !ok {
            break
        }
    }

}

func Write(intChan chan int)  {
    for i := 0; i < 50; i++ {
        intChan <- i
        fmt.Println("Write data:",i)
    }
    close(intChan)
}

func Read(intChan chan int,exitChan chan bool)  {
    for {
        v, ok := <- intChan
        if !ok {
            break
        }
        fmt.Println("Read data",v)

    }

    exitChan <- true
    close(exitChan)
}
```

## 单元测试

```go
/* 要开始一个单元测试，需要准备一个 go 源码文件，在命名文件时需要让文件必须以_test结尾。默认的情况下，go test命令不需要任何的参数，它会自动把你源码包下面所有 test 文件测试完毕，当然你也可以带上参数。*/
```

