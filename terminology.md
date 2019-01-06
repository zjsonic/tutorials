# Terminology
## AJAX

## Reliable Data Transfer(可靠的数据传输)
《HTTP权威指南》P25:
>HTTP使用的是可靠的数据传输协议，因此即使数据来自地球的另一端，它也能够确保数据在传输的过程中不会被损坏或产生混轮。

## shell
shell就是充当人与计算机之间的翻译官。
因为在Linux中图形界面不是很强，一般都只是直接通过命令窗口来进行系统控制的，所以shell就显得特别重要。你也可以简单的将shell理解为命令行，与之相关的还有shell脚本，就是shell能识别的一连串命令行。说了那么多，来看个官方定义

>Unix shell：一种壳层与命令行界面，是Unix操作系统下传统的用户和计算机的交互界面。普通意义上的shell就是可以接受用户输入命令的程序。它之所以被称作shell是因为它隐藏了操作系统低层的细节。Unix操作系统下的shell既是用户交互的界面，也是控制系统的脚本语言。


- [https://www.jianshu.com/p/a702a01db5c7](https://www.jianshu.com/p/a702a01db5c7)


## bash

bash是shell的一种，在早年的UNIX年代，发展者众多，所以就有许多不同的版本，例如Bourne shell（sh），这也是必然的，每种shell都有其应用的需求，很难说孰好孰坏。而在Linux中默认的shell就是Bourne-Again shell(简称bash)，所以学习linux就必须要掌握bash的用法。另外一个是伯克利分校比尔▪乔伊写的C  Shell(csh)，因为类似C语言，故此得名。而由这两种又发展出很多其它的版本，不过根基都在这里。

## 工厂函数
- 工厂函数是一个最后返回值是对象的函数，但它既不是类，也不是构造函数。
- 在JavaScript中，任何函数都可以返回一个对象。 但当函数没有使用new关键字时，那它便是一个工厂函数。
