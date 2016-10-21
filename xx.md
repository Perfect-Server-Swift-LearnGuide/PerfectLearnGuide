### 了解使用Swift编译系统

Swift 编译系统为编译库、可执行文件和在不同工程之间共享代码提供了基本的约定。

创建一个新的 Swift 包，首先创建并进入到一个新的目录命名为 Hello ：

$ mkdir Hello
$ cd Hello
每个包在其根目录下都必须拥有一个命名为 Package.swift 清单文件。如果清单文件为空，那包管理器将会使用常规默认的方式来编译包。创建一个空的清空文件使用命令：

$ touch Package.swift
当使用默认方式时，包管理器预计将包含在 Sources/ 子目录下的所有源代码。创建方式：

$ mkdir Sources
编译可执行文件

默认方式下，目录中包含一个文件称为 main.swift 将会将文件编译成与包名称相同的二进制可执行文件。

在这个例子中，包将生成一个可以输出 Hello, world! 的可执行文件命名为 Hello 。

在 Sources/ 目录下创建一个命名为 main.swift 的文件，并使用你喜欢的任意一种编辑器输入如下代码：

print("Hello, world!")
返回到 Hello 目录中，通过运行 swift build 命令来编译包：

$ swift build
当命令完成之后，编译产品将会出现在 .build 目录中。通过如下命令运行 Hello 程序:

$ .build/debug/Hello
Hello, world!