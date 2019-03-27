# 8cc C编译器
8cc是一个C语言编译器，在支持C11特性的基础上，尽力保持了代码的精简。

这个编译器支持编译自身的源码，所以它既是C语言的一个实现也可以说是该编译器可以编译的代码

8cc的源代码被精心编写以尽可能易读易理解，所以这份代码可以当作很好的材料来学习编译器的各种姿势技巧。在学习C的源码在各阶段是如何被处理的时，你或许会发现词法分析器，预处理器，解析器已经足够有用。

这不是一个善于优化的编译器。生成的代码的运行时间通常为GCC的两倍或更长。我计划在将来实现一个力所能及的优化。

8cc只支持x86-64类型的linux。 在我解决所有已知的错误编译和实现一个优化阶段前，我没有打算让这个编译器变得可移植。 2015年，我使用Ubuntu 14作为我的开发平台。但是该编译器应该可以在其他x86-64 Linux的发行版上工作。

注意：不要对这个编译器有太大期待。如果你试图编译一个其他程序（非该编译器代码），很有可能你会发现编译错误或误编译。 因为这只是一个单人项目，目前我只是用了我几个月里的空闲时间来做而已。

## Build
使用make来构建
```bash
make
```
8cc 有单元测试，要运行这些测试，使用test作为参数
```bash
make test
```
下面这个目标会构建8cc三次来检查第一阶段的编译器可以编译出第二阶段的编译器，而第二阶段的编译器可以编译出第三阶段的编译器。 然后它会比较阶段二编译器和阶段三的编译器， 一个字节一个字节的比较来检查我们是否达到了固定点。（译注：迭代到。。。稳定的版本）

## Author
Rui Ueyama <mail>rui314@gmail.com</mail>

## C编译器开发的有关链接
除了一些编译的著名书籍，如，龙书，我发现下面这些书/文档在开发一个C编译器时十分有用。注意标准草稿版本和正式版本十分类似。你可以实际把他们当作标准文档使用。
- LCC: A Retargetable C Compiler: Design and Implementation http://www.amazon.com/dp/0805316701, https://github.com/drh/lcc
- TCC: Tiny C Compiler http://bellard.org/tcc/, http://repo.or.cz/w/tinycc.git/tree
- C99 standard final draft http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1124.pdf
- C11 standard final draft http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1570.pdf
- Dave Prosser's C Preprocessing Algorithm http://www.spinellis.gr/blog/20060626/
- The x86-64 ABI http://www.x86-64.org/documentation/abi.pdf
