+++
title = 'C++ Primer 第五版 2.1  笔记'
date = 2024-09-13T20:36:03+08:00
categories = []
tags = ["C++ Primer", "Bilibili", "C++", "技术", "读书笔记"]
+++

这一集视频我们来看一下第二章的第一节。从这一集视频开始，我决定只讲代码。而且基本只讲书上出现过的代码，实在有需要我再自己补充代码。因为基础知识的话，我觉得书上写的已经足够详细了，我再复述一遍没什么太多的意义。

而代码是更加直观的东西，并且，我们最终都是要去实际地写代码的。所以，我这里将着重去讲解书上出现的每一处代码。

首先看前言部分，

```cpp
i = i + j;
```

这里还要额外多说一点，就是，从这一章开始，我在视频中演示代码所使用的编辑器将换到 neovim + neovide 这样一个组合，然后，在 Windows 平台下，我会使用 pwsh 也就是 powershell 脚本来进行自动化编译和运行，而在 Linux 中，我将使用 shell 脚本来自动化编译和运行。当然，构建工具使用的肯定是 cmake。

## Part1 算数类型

这里我们只去讲如何在程序中使用这些类型，关于其背后的原理，我想，大家会在计算机组成原理中得到详细的解释，当然，如果我有时间的话，可能会出视频讲一下，毕竟，大学里面的老师很有可能会因为课时不足，导致在课堂上也无法讲清楚。

当然，如果有时间的话，推荐大家去看《深入理解计算机系统(第三版)》这本书，英文名是：Computer Systems: A Programmer's Perspective (3rd Edition)，也就是大名鼎鼎的 CSAPP。就拿浮点数来说，这个是我当时完整看过的，所以能够安心地给出评价，那就是如果你想理解浮点数真正的构造及原理，那么，可以抽空看一下[这本书](https://book.douban.com/subject/26912767)。

那么，如果仅仅停留在本书需要理解的程度，那么，我们写几行代码就可以了解怎么去使用了，

```cpp
#include <iostream>

int main()
{
    // bool 类型，通常大小为 1 个字节
    bool boolean = true;
    std::cout << "bool: " << boolean << " (size: " << sizeof(boolean) << " bytes)" << std::endl;

    // char 类型，8 bits
    char character = 'A';
    std::cout << "char: " << character << " (size: " << sizeof(character) << " bytes)" << std::endl;

    // wchar_t 类型，宽字符，16 bits 或 32 bits，取决于平台
    wchar_t wide_character = L'A';
    std::wcout << "wchar_t: " << wide_character << " (size: " << sizeof(wide_character) << " bytes)" << std::endl;

    // char16_t 类型，16 bits Unicode 字符
    char16_t unicode_16 = u'A';
    std::wcout << "char16_t: " << static_cast<wchar_t>(unicode_16) << " (size: " << sizeof(unicode_16) << " bytes)" << std::endl;

    // char32_t 类型，32 bits Unicode 字符
    char32_t unicode_32 = U'A';
    std::wcout << "char32_t: " << static_cast<wchar_t>(unicode_32) << " (size: " << sizeof(unicode_32) << " bytes)" << std::endl;

    // short 整数类型，16 bits
    short short_integer = 16;
    std::cout << "short: " << short_integer << " (size: " << sizeof(short_integer) << " bytes)" << std::endl;

    // int 整数类型，通常至少为 32 bits，但某些系统上可能为 16 bits
    int integer = 26;
    std::cout << "int: " << integer << " (size: " << sizeof(integer) << " bytes)" << std::endl;

    // long 整数类型，通常为 32 bits
    long long_integer = 36;
    std::cout << "long: " << long_integer << " (size: " << sizeof(long_integer) << " bytes)" << std::endl;

    // long long 整数类型，64 bits
    long long long_long_integer = 46LL;
    std::cout << "long long: " << long_long_integer << " (size: " << sizeof(long_long_integer) << " bytes)" << std::endl;

    // float 单精度浮点数，精度为 6 位有效数字
    float single_precision = 3.1f;
    std::cout << "float: " << single_precision << " (size: " << sizeof(single_precision) << " bytes, precision: " << FLT_DIG << " significant digits)" << std::endl;

    // double 双精度浮点数，精度为 10 位有效数字
    double double_precision = 3.14;
    std::cout << "double: " << double_precision << " (size: " << sizeof(double_precision) << " bytes, precision: " << DBL_DIG << " significant digits)" << std::endl;

    // long double 扩展精度浮点数，通常与 double 相同，但某些系统上可能有更高精度
    long double extended_precision = 3.1415L;
    std::cout << "long double: " << extended_precision << " (size: " << sizeof(extended_precision) << " bytes, precision: " << LDBL_DIG << " significant digits)" << std::endl;

    return 0;
}
```

使用微软的 MSVC 编译器运行的结果如下，

```cpp
bool: 1 (size: 1 bytes)
char: A (size: 1 bytes)
wchar_t: A (size: 2 bytes)
char16_t: A (size: 2 bytes)
char32_t: A (size: 4 bytes)
short: 16 (size: 2 bytes)
int: 26 (size: 4 bytes)
long: 36 (size: 4 bytes)
long long: 46 (size: 8 bytes)
float: 3.1 (size: 4 bytes, precision: 6 significant digits)
double: 3.14 (size: 8 bytes, precision: 15 significant digits)
long double: 3.1415 (size: 8 bytes, precision: 15 significant digits)
```

观察 double 类型，大于书上所说的 10 位有效数字，也就可以理解书上所说，C++ 标准只是规定了尺寸的最小值，各个编译器可以自己再行发挥。

然后关于有符号和无符号类型的区别，大家如果想仔细理解的也可以去看 CSAPP。其他的一些不难理解的细节，比如，书上讲的，

> 通常，float以1个字（32比特）来表示，double以2个字（64比特）来表示，long double以3或4个字（96或128比特）来表示。一般来说，类型float和double分别有7和16个有效位；

不是刚刚才有一个表格说是 6 位和 10 位吗？怎么又变了？**注意**，依然是这个问题，人家表格说的是最小尺寸。

还有 char, signed char 和 unsigned char 的细节问题，这些都是容易理解的、白话一样的内容。

## Part2 类型转换

```cpp
#include <iostream>

int main(int argc, char *argv[])
{
    bool b = 42; // b is true
    std::cout << b << std::endl;
    int i = b; // i has value 1
    std::cout << i << std::endl;
    i = 3.14; // i has value 3
    std::cout << i << std::endl;
    double pi = i; // pi has value 3.0
    std::cout << pi << std::endl;
    unsigned char c = -1; // assuming 8-bit chars, c has value 255
    std::cout << c << std::endl;
    std::cout << static_cast<int>(c) << std::endl;
    signed char c2 = 256; // assuming 8-bit chars, the value of c2 is undefined
    std::cout << c2 << std::endl;
    std::cout << static_cast<int>(c2) << std::endl;
    return 0;
}
```

```cpp
#include <iostream>

int main(int argc, char *argv[])
{
    int i = 42;
    std::cout << i << std::endl;
    if (i) // condition will evaluate as true
        i = 0;
    std::cout << i << std::endl;
    return 0;
}
```

注意，虽然可以进行如此的类型转换，但是实际的使用过程中还是建议按照规范来，尽量不要让程序去做自动的类型转换，因为可能会遇到移植性的问题。


