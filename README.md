# GoLang

### brew install go (brew uninstall go)

'''bash

    ==> Downloading https://homebrew.bintray.com/bottles/go-1.7.4.el_capitan.bottle.tar.gz
    ######################################################################## 100.0%
    ==> Pouring go-1.7.4.el_capitan.bottle.tar.gz
    ==> Caveats
    As of go 1.2, a valid GOPATH is required to use the `go get` command:
    https://golang.org/doc/code.html#GOPATH
    You may wish to add the GOROOT-based install location to your PATH:
    export PATH=$PATH:/usr/local/opt/go/libexec/bin
    ==> Summary
    🍺  /usr/local/Cellar/go/1.7.4: 6,435 files, 250.6M

    export PATH=$PATH:/usr/local/opt/go/libexec/bin
'''

#### 从提示中可以看出需要设置GOPATH和GOROOT的环境变量，以及设置PATH.

## 配置GOPATH

'''bash

    go env
    GOARCH="amd64"
    GOBIN=""
    GOEXE=""
    GOHOSTARCH="amd64"
    GOHOSTOS="darwin"
    GOOS="darwin"
    GOPATH=""
    GORACE=""
    GOROOT="/usr/local/Cellar/go/1.7.4_1/libexec"
    GOTOOLDIR="/usr/local/Cellar/go/1.7.4_1/libexec/pkg/tool/darwin_amd64"
    CC="clang"
    GOGCCFLAGS="-fPIC -m64 -pthread -fno-caret-diagnostics -Qunused-arguments -fmessage-length=0 -fdebug-prefix-map=/var/folders/ql/b68jtl1d5xqdcw9bct4kkvdr0000gn/T/go-build046467341=/tmp/go-build -gno-record-gcc-switches -fno-common"
    CXX="clang++"
    CGO_ENABLED="1"
'''

## 在fishshell设置GOPATH：
'''bash

    set -gx GOPATH /usr/local/Cellar/go/1.7.6
'''

## 在bash中设置：
'''bash

    sudo vim .bash_profile

    export GOPATH=/usr/local/Cellar/go/1.7.6
    export GOBIN=$GOPATH/bin
    export PATH=$PATH:$GOBIN
'''

## 使修改立刻生效:
'''bash

    source .bash_profile

    go env
'''

## 环境变量设置完成!




## Visual Studio Code 工作区设置
'''bash

    {
    // Go configuration
    "go.gopath": "/Volumes/WorkDate/Project/Golang/Gocode",
    "go.goroot": "/usr/local/Cellar/go/1.7.4_1/libexec",
    }
'''

# HTTP-Proxy.go 测试程序

'''bash

    cd /Volumes/WorkDate/Project/Golang/
    
    // go 编译
    go build HTTP-Proxy.go
'''