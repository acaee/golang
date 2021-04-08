# 第一章 入门指南

## 中文资料

中文社区：[https://learnku.com/go](https://learnku.com/go)

中文标准库文档：[https://studygolang.com/pkgdoc](https://studygolang.com/pkgdoc)

设计模式：[https://github.com/jianyuecc/go-patterns](https://github.com/jianyuecc/go-patterns)

## Go语言关键概念

### `gopath`

```text
bin/ # 编译后的可执行二进制文件
pkg/ # 编译好的库文件
src/ # go源码文件
```

### `goroot`

> Golang的安装目录

```text
/bin：包含可执行文件，如：编译器，Go 工具
/doc：包含示例程序，代码工具，本地文档等
/lib：包含文档模版
/misc：包含与支持 Go 编辑器有关的配置文件以及 cgo 的示例
/os_arch：包含标准库的包的对象文件（.a）
/src：包含源代码构建脚本和标准库的包的完整源代码（Go 是一门开源语言）
/src/cmd：包含 Go 和 C 的编译器和命令行脚本
```

### `GO111MODULE`

golang version 1.12

```text
GO111MODULE=on #启用go module
GO111MODULE=off #禁用go module
GO111MODULE=auto #自动模式
    当工作区位于 GOPATH 之外时，GO111MODULE=on
    当工作区位于 GOPATH 之内时，GO111MODULE=off
```

### 修改Golang环境变量

```text
# 修改go env
go env -w GOPROXY=https://mirrors.aliyun.com/goproxy,direct
go env -w GO111MODULE=auto
```

### `gofmt`

Golang的代码格式化工具

```text
-d 显示差异而不是重写文件

-e 报告所有错误（不只是不同行的前10个错误）

-l 列出格式与gofmt不同的文件

-R 字符串
    重写规则（例如“a[b:len（a）]->a[b:''）

-S 简化代码

-w 将结果写入（源）文件而不是stdout
```

### `godoc`

Golang的文档工具

```text
godoc -http=localhost:6060
```

### `go mod`

Golang的依赖管理工具

| 命令 | 说明 |
| :---: | :---: |
| download | 下载依赖包 |
| edit | 编辑go.mod |
| graph | 打印模块依赖图 |
| init | 初始化mod |
| tidy | 拉取缺少的模块，移除不用的模块 |
| vendor | 将依赖赋值到vendor下 |
| verify | 验证依赖是否正确 |
| why | 解释为什么需要依赖 |

