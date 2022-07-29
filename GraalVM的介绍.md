## GraalVM的介绍

**GraalVM是一款用来加速使用Java或者其他虚拟机语言编写应用执行的高性能JDK，同时也支持对JavaScrip、Python以及一众热门语言的运行时。GraalVM提供了两种运行Java应用的方式—通过使用Graal即时编译器在HotSpot虚拟机中运行或提前（AOT）编译为本机可执行文件运行。GraalVM的多语言能力使得在单个应用程序中混合多种编程语言成为可能，同时消除了不同语言的调用成本。**



<br/>



## GraalVm的架构图

![graalvm_architecture_community](/Users/kazama/Desktop/graalvm_architecture_community.png)

**GraalVM向HotSpotVM添加了一个用Java编写的高级即时优化编译器（JIT）。除了运行Java和基于JVM类型的语言，GraalVM的语言实现框架（Truffle）还可以让JavaScript、Ruby、Python等语言运行在JVM上。通过GraalVM Truffle，Java和其他支持的语言可以直接相互操作，并在同一内存空间中来回传递数据。**



<br/>



## 运行模式

> **GraalVM作为一种很独特的运行环境，提供了几种操作模式：JVM运行时模式，原生可执行文件模式，Java on Truffle（相同的Java应用程序可以在任何一种模式上运行）**



### JVM运行模式

**当在HotSpot虚拟机上运行程序时，GraalVM默认使用GraalVM编译器作为顶层即时编译器（JIT）。在运行的时候，一个应用在JVM中被正常的加载和执行，JVM将Java或任何其他JVM本地语言的字节码传递给编译器，编译器将其编译为机器码并返回给JVM。在Truffle框架上编写的受支持语言的解释器本身就是在JVM上运行的Java程序。**



### 本地镜像

**Native Image是一项创新技术，它将Java代码编译成独立的本机可执行文件或本机共享库。在构建本机可执行文件期间会将所有的应用程序类、依赖项、第三方依赖库和所需要的任何JDK类的字节码进行处理。并且所生成的本机可执行文件并不依赖每个操作系统中的JVM**



### Java on Truffle

**Java on Truffle是Java虚拟机规范的实现，使用Truffle语言实现了框架构建。它是一个完整的JVM，包括所有的核心组件，实现了和JRE库相同的API，并且重用了来自GraalVM的所有JAR和本地库。**



<br/>



## 可用的已发行版本

**GraalVM提供GraalVM企业版和GraalVM社区版，并包括对Java 11和Java 17的支持。GraalVM 企业版是基于Oracle JDK，而GraalVM社区版基于OpenJDK。**

**GraalVM可用于x86 64位和ARM 64位系统上的Linux和MacOS，以及x86 64位系统上的Windows。**
**根据平台的不同，发行版以.tar.gz或.Zip存档的形式发布。有关安装说明，请参阅入门指南。**



<br/>



## 发行组件列表

> **GraalVM由核心组件和附加组件组成。**
> **核心组件支持将GraalVM用作以基于JVM的语言或可嵌入多语言应用程序编写的程序运行平台。**



### 核心组件

- **Java HotSpot VM**
- **Graal编译器—顶层的JIT编译器**
- **Polyglot API—用于在共享运行时中组合编程语言的API**
- **GraalVM Updater—用于安装附加功能的实用程序**



### 附加组件

> **GraalVM核心安装可以使用更多语言运行时和实用程序进行扩展。**



**工具/实用程序**

- **本机镜像—将应用程序提前编译为本机平台可执行文件的技术。**
- **LLVM工具链—一组用于将本地程序编译为可在GraalVM上执行的位码的工具和API**



**支持的运行时**

- **使用JavaScript REPL和JavaScript解释器的JavaScript运行时**
- **Node.js—用于JavaScript的Node.js 16.14.2运行时**
- **带有lli工具的LLVM运行时，可以直接用LLVM位码执行程序**
- **Java on Truffle—一种构建在Truffle框架上的JVM实现，通过字节码解释器运行Java**
- **Python—和Python 3.8.5 兼容**
- **Ruby—和Ruby 3.0.3 兼容**
- **R—和 GNU R 4.0.3 兼容**
- **GraalWasm—Web 组件**



<br/>



## 许可和支持

**GraalVM Community Edition是基于GitHub上可用的源代码构建的开源软件，并在GNU通用公共许可证的第2版下发布，带有“Classpath”例外，这和Java相同。检查单个GraalVM组件的许可，它们通常派生于特定语言的许可，并且可能存在差异。GraalVM Community可以免费用于任何目的，没有任何附加条件，但也没有保证或支持。**



<br/>



## 功能的支持

**GraalVm技术是以生产就绪和实验性的形式发布**

**我们正在考虑为GraalVM的未来版本提供一些实验特性，这些特性并不打算用于生产环境中。开发团队欢迎大家对这些实验特性的反馈，但用户应该意识到，实验特性可能永远不会包含在最终版本中，或者可能在投产之前会发生重大改变**

**下表按照平台列出了GraalVM Community Edition 22.1中已用于生产或者实验性特性**

| Feature         | Linux AMD64  | Linux ARM64   | macOS        | macOS ARM64   | Windows       |
| :-------------- | :----------- | :------------ | :----------- | :------------ | :------------ |
| Native Image    | stable       | stable        | stable       | experimental  | stable        |
| LLVM runtime    | stable       | stable        | stable       | experimental  | not available |
| LLVM toolchain  | stable       | stable        | stable       | experimental  | not available |
| JavaScript      | stable       | stable        | stable       | experimental  | stable        |
| Node.js         | stable       | stable        | stable       | not available | stable        |
| Java on Truffle | experimental | experimental  | experimental | experimental  | experimental  |
| Python          | experimental | not available | experimental | not available | not available |
| Ruby            | experimental | experimental  | experimental | experimental  | not available |
| R               | experimental | not available | experimental | not available | not available |
| WebAssembly     | experimental | experimental  | experimental | experimental  | experimental  |



<br/>



## 接下来读什么

**如果你是GraalVM的新手或者使用它的经验很少，继续使用`GraalVM入门`。在你的本地机器上安装GraalVM，尝试运行指南中提供的示例，或者用你的工作负载测试GraalVM。之后，我们建议您看看更复杂的`示例应用程序`。**

**已经安装了GraalVM或有使用经验的开发人员，可以跳过入门指南，继续阅读`参考手册`来深入了解GraalVM技术。**

**要开始使用GraalVM Polyglot API编码，请查看`《GraalVM SDK Java API参考》`。**

**如果你不能在文档中找到你需要的答案或有一个故障需要排除，你可以在一个`slack channel`中寻求帮助或提交一个GitHub问题。**