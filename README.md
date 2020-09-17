# aliyundts


Go语言提供了简单的demo。
核心是如何选取avro的序列化/反序列化代码生成器
这边使用 https://github.com/actgardner/gogen-avro 来生成本地解析代码

go环境的安装这里使用了 1.13.4版本
代理如下
go env -w GOPROXY=https://goproxy.io,direct
GOPATH 为 $HOME/go

1.首先安装解析工具
go install github.com/actgardner/gogen-avro/v7/cmd/...

到下载目录可以看到
$HOME/go/bin/gogen-avro
假设我们生成的反序列化代码为 dtsvaro
运行命令为
mkdir dtsavro && gogen-avro  --package=dtsavro ./dtsavro ./avro/Record.avsc


这个命令意思是我们使用Record.asvc文件，生成package 为 dtsavro 的文件，生成到~/dtsavro目录下

2.接下来我们运行工程
使用 go mod tidy 来加载依赖
这个时候dtsavro可能找不到
拷贝上面生成的~/dtsavro目录到 $GOPATH的src下面，找到之后代码就不会有报错了，就可以调试了
