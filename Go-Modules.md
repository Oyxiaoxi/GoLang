# Go Modules

> Go Modules 是 Go 语言的代码一开管理工具。类似于 PHP 中的 Composer、Node.js 中的 npm 。
>
> Go Modules 由官方维护。自 Go 版本 1.14 开始，官方鼓励所有用户迁移到 Go Modules 以进行依赖项管理。

## 弃用 $GOPATH

> Go Modules 出现的目的之一就是为了解决 GOPATH 的问题。
>
> 在 $GOPATH 时代，Go 源码必须放置于 `$GOPATH/src` 下，抛弃 $GOPATH 的好处，是你能在任意地方创建的 Go 项目。
>
> $GOPATH 有非常落后的依赖管理系统。因在执行 `go get` 时，无法传达任何版本信息。
>
> 在构建 Go 应用程序上，我们无法保证其它人与你所期望依赖的第三方库是相同的版本（相同的代码），也就是说无法保证所有人的依赖版本都一致。

## Go Modules 日常使用

1. 初始化

   ```bash
   go mod init
   ```

2. Go Proxy

   ```bash
   go env -w GOPROXY=https://goproxy.cn
   go get github.com/julienschmidt/httprouter
   ```

3. go.mod

   每一次的 `go get` 都会同时修改 `go.mod` 和 `go.sum` 文件。

   go.mod

   ```go
   module github.com/summerblue/goblog
   
   go 1.15
   
   require (
       github.com/gorilla/mux v1.7.4
       github.com/julienschmidt/httprouter v1.3.0 // indirect
   )
   ```

   参数：

   - module —— 我们的 goblog 在 Go Module 里也算是一个 Module ；
   - go —— 指定了版本要求，最低 1.14
   - require —— 是项目所需依赖

4. go.sum

   `go.sum` 文件保存着依赖包的版本和哈希值：

   ```go
   github.com/gorilla/mux v1.7.4 h1:VuZ8uybHlWmqV03+zRzdwKL4tUnIp1MAQtp1mIFE1bc=
   github.com/gorilla/mux v1.7.4/go.mod h1:DVbg23sWSpFRCP0SfiEN6jmj59UnW/n46BH5rLB71So=
   github.com/julienschmidt/httprouter v1.3.0 h1:U0609e9tgbseu3rBINet9P48AI/D3oJs4dN7jwJOQ1U=
   github.com/julienschmidt/httprouter v1.3.0/go.mod h1:JR6WtHb+2LUe8TCKY3cZOxFyyO8IZAc4RVcycCCAKdM=
   ```

5. indirect

   此标志标明这个依赖包还未被使用

   ```go
   require (
       github.com/gin-gonic/gin v1.6.3 // indirect
       github.com/gorilla/mux v1.7.4
       github.com/julienschmidt/httprouter v1.3.0 // indirect
   )
   ```

6. tidy

   此命令做整理依赖使用，执行时会把未使用的 module 移除掉

   ```
   go mod tidy
   ```

7. 包存放位置

   `$GOPATH/pkg/mod`

8. 清空 Go Modules 缓存

   ```bash
   go clean -modcache
   ```

9. 下载依赖

   默认情况下，当 `go run` 和 `go build` 命令执行时，Go 会基于自动 `go.mod` 文件自动拉取依赖。

   ```bash
   go mod download
   ```

# 命令合集

| **命令**        | **作用**                         |
| --------------- | -------------------------------- |
| go mod init     | 生成 go.mod 文件                 |
| go mod download | 下载 go.mod 文件中指明的所有依赖 |
| go mod tidy     | 整理现有的依赖                   |
| go mod graph    | 查看现有的依赖结构               |
| go mod edit     | 编辑 go.mod 文件                 |
| go mod vendor   | 导出项目所有的依赖到 vendor 目录 |
| go mod verify   | 校验一个模块是否被篡改过         |
| go mod why      | 查看为什么需要依赖某模块         |

