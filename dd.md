### Mac开发环境搭建

首先先检查自己的Mac电脑是否安装有Swift工具包

1.在终端运行

```ruby

swift --version

```

若显示如下信息则表明已安装完成，如果你的电脑中安装有Xcode，Swift工具包会包含其中，目前Swift已发布最新版3.0，请注意您需要最新版本的Swift 3.0。如果低于3.0版本则Perfect是无法成功编译的。

```ruby

Apple Swift version 3.0 (swiftlang-800.0.46.2 clang-800.0.38)

Target: x86_64-apple-macosx10.9

```

如果你的电脑中安装有多个版本的Xcode，因为Swift更新较为频繁，不同的Xcode版本对应的Swift版本一般也会不同，比如电脑中同时包含Xcode7.3和Xcode8，可以使用‘xcode-select’工具选择默认版本，具体指令如下,具体的Xcode名字以自己的为准

```ruby

sudo xcode-select -switch /Applications/Xcode8.app/Contents/Developer

```

2.终端Swift使用初体验

使用swift指令，可以在终端边写边查看运行结果，类似Xcode的Playground功能。

swift指令可以将输入的Swift代码同步解析并运行。

在终端中输入如下指令，进入Swift代码编辑环境，代码换行使用Command+Enter组合键，结束编辑状态，使用Command+D组合键，清楚屏幕代码使用指令**clear**

```ruby

swift

```

```ruby

 1> let str = "hello swift"

str: String = "hello swift"

 2> func add(a: Int, b: Int) -> Int {

 3.    return a + b

 4. }

 5> add(a: 2, b: 3)

$R0: Int = 5

```

3.搭建Mac服务器环境

** 让我们先来编译Perfect提供的入门项目 **

执行以下命令能够克隆并编译一个空的入门项目。编译后可以启动一个本地的服务器，监听您计算机的8181端口：

```ruby

git clone https://github.com/PerfectlySoft/PerfectTemplate.git

cd PerfectTemplate

swift build

.build/debug/PerfectTemplate

```

您应该可以在终端控制台中看到类似下面的内容：

```ruby

Starting HTTP server on 0.0.0.0:8181 with document root ./webroot

```

服务器现在已经运行并等待连接。从浏览器打开[http://localhost:8181/](http://localhost:8181/) 可以看到欢迎信息。在终端控制台中输入组合键“control-c”可以随时终止服务器运行。

完整的源代码请参考PerfectTemplate项目模板。

** 用Xcode来启动一个本地服务器 **

首先创建一个目录，来保存创建的工程项目，运行以下指令

```ruby

mkdir FirstPerfectDemo

```

然后进入到该目录

```ruby

cd FirstPerfectDemo

```

接下来介绍:Swift软件包管理器（SPM），它能够创建一个Xcode项目，并且能够运行PerfectTemplate模板服务器，还能为你的项目提供完全的源代码编辑和调试。在您的终端命令行内输入：

```ruby

swift package generate-xcodeproj

```

然后打开产生的文件“PerfectTemplate.xcodeproj”，确定选择了可执行的目标文件，并选择在“我的Mac”运行。现在您可以运行并调试服务器了。

直接运行上述指令你可能会发现如下错误：

```ruby

error:: no Package.swift found

```

提示我们需要一个名为Package.swift的文件

