+++
title = 'C++ Primer 第五版 2.1  笔记'
date = 2024-09-13T20:36:03+08:00
categories = []
tags = ["C++ Primer", "Bilibili", "C++", "技术", "读书笔记"]
+++

这一集视频我们来看一下第二章的第一节。从这一集视频开始，我决定只讲代码和我认为需要挑出来讲解的难点/细节，对于难点和细节，我决定以提出问题和解决问题的形式来呈现。关于代码，基本只讲书上出现过的代码，实在有需要我再自己补充代码。毕竟基础知识的话，我觉得书上写的已经足够详细了，我再复述一遍没什么太多的意义，所以，大家看书的话，常看常新呀，总之就是一定要常看。

因为代码是更加直观的东西，并且，我们最终都是要去实际地写代码的。所以，我这里将着重去讲解书上出现的每一处代码，我认为能够理解代码，并且把这些代码实际应用到我们实际的项目中去，这才是真正有意义的事情。

如果我们能做到完全理解书上的这些代码，做到看到这些代码时心中有底，我觉得那就是胜利。同时，如果习题里面有涉及代码的部分，我们也不会错过。

尽量做到：一切都在代码中。这样，如果有人问，你读过这本书吗？我们可以很有底气地说，读过，毕竟，代码全都掌握了，难道还不算读过吗？

这里还要额外多说一点，就是，从这一章开始，我在视频中演示代码所使用的编辑器将换到 neovim + neovide 这样一个组合，然后，在 Windows 平台下，我会使用 pwsh 也就是 powershell 脚本来进行自动化编译和运行，而在 Linux 中，我将使用 shell 脚本来自动化编译和运行。当然，构建工具使用的肯定是 cmake。

那么，就直接看代码吧。

说明：代码的命名规范依然以英文原版书中出现的代码的页码为指导原则。

## Part1 

英文原书 p32,

```cpp
#include <iostream>

int main()
{
    int i = 1;
    int j = 2;
    i = i + j;
    std::cout << i << std::endl;

    return 0;
}
```

个人对英文原书 32 页补充代码，custom_p32.cpp,

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

关于这些基本类型，如果有时间的话，推荐大家去看《深入理解计算机系统(第三版)》这本书，英文名是：Computer Systems: A Programmer's Perspective (3rd Edition)，也就是大名鼎鼎的 CSAPP。就拿浮点数来说，这个是我当时完整看过的，所以能够安心地给出评价，那就是如果你想理解浮点数真正的构造及原理，那么，可以抽空看一下[这本书](https://book.douban.com/subject/26912767)。

那么，如果仅仅停留在本书需要理解的程度，那么，我们就像上面这样写几行代码就可以了解怎么去使用了，

使用微软的 MSVC 编译器运行的结果如下，

```shell
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

这里为什么有些尺寸感觉和书上有差异呢？因为书上写的是标准规定的只是最小尺寸，然后在此基础上编译器可以自由发挥。

## Part2 类型转换

p35,

```cpp
#include <iostream>

int main()
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

p36_1,

```cpp
#include <iostream>

int main()
{
    int i = 42;
    std::cout << i << std::endl;
    if (i) // condition will evaluate as true
        i = 0;
    std::cout << i << std::endl;
    return 0;
}
```

p36_2,

```cpp
#include <iostream>

int main()
{
    unsigned u = 10;
    int i = -42;
    std::cout << i + i << std::endl; // prints -84
    std::cout << u + i << std::endl; // if 32-bit ints, prints 4294967264

    return 0;
}
```

这里书上的解释有点问题，英文原版里面是让我们去看上面的案例，这里中文翻译多给了一些解释，但是这个解释不太能够让人理解，我们还是按照上面的取模的解释来。而对于给负数取模，我们可以把其想象成反方向拨动时钟，然后，从 0 到指针之间的距离就是我们所求的取模后的余数。

p37_01,

```cpp
#include <iostream>

int main()
{
    unsigned u1 = 42, u2 = 10;
    std::cout << u1 - u2 << std::endl; // ok: result is 32
    std::cout << u2 - u1 << std::endl; // ok: but the result will wrap around

    return 0;
}
```

p37_02,

```cpp
// 这里需要看一下中文版 p11 也的练习题第 2 题
#include <iostream>

int main(int argc, char *argv[])
{
    for (int i = 10; i >= 0; --i)
        std::cout << i << std::endl;

    return 0;
}
```

按：这里可以到 1.4.1 节(英文 p13)的练习那里去看一下。

p37_03,

```cpp
#include <iostream>

int main()
{
    /*
    // WRONG: u can never be less than 0; the condition will always succeed
    for (unsigned u = 10; u >= 0; --u)
        std::cout << u << std::endl;
    */
    return 0;
}
```

p37_04,

```cpp
#include <iostream>

int main()
{
    unsigned u = 11; // start the loop one past the first element we want to print
    while (u > 0)
    {
        --u; // decrement first, so that the last iteration will print 0
        std::cout << u << std::endl;
    }

    return 0;
}
```

## Part3 字面值常量

p38_01,

```cpp
#include <iostream>

int main()
{
    int a = 20;   // 十进制
    int b = 024;  // 八进制
    int c = 0x14; // 十六进制
    std::cout << a << ", " << b << ", " << c << std::endl;
    return 0;
}
```

p38_02,

```cpp
#include <iostream>

int main()
{
    double a = 3.14159;
    double b = 3.14159E0;
    double c = 0.;
    double d = 0e0;
    double e = .001;
    std::cout << a << ", " << b << ", " << c << ", " << d << ", " << e << std::endl;
    return 0;
}
```

p39_01,

```cpp
#include <iostream>
#include <string>

int main()
{
    char a = 'a';
    std::string b = "Hello World!";
    std::cout << a << ", " << b << std::endl;
    return 0;
}
```

p39_02,

```cpp
#include <iostream>

int main()
{
    // multiline string literal
    std::cout << "a really, really long string literal "
                 "that spans two lines" << std::endl;
    return 0;
}
```

p39_03,

```cpp
#include <cstdio>
#include <iostream>

int main()
{
    std::cout << "Hello\nWorld" << std::endl;
    std::cout << "Name\tAge" << std::endl;
    std::cout << "\a" << std::endl;
    std::cout << "Hello\vWorld" << std::endl;
    std::cout << "Helloo\b World" << std::endl;
    std::cout << "He said, \"Hello!\"" << std::endl;
    std::cout << "C:\\Program Files" << std::endl;
    std::cout << "What\?" << std::endl;
    std::cout << "It\'s a cat" << std::endl;
    std::cout << "Hello\rWorld" << std::endl;
    std::cout << "Hello\fWorld" << std::endl;
    getchar();
    return 0;
}
```

p39_04,

```cpp
#include <iostream>

int main()
{
    std::cout << '\n';      // prints a newline
    std::cout << "\tHi!\n"; // prints a tab followd by "Hi!" and a newline
    return 0;
}
```

p39_05,

```cpp
#include <iostream>

int main()
{
    std::cout << "\7";            // 在一些环境下会发出提示音，和 \a 相同
    std::cout << "Hello\12World"; // 输出：
                                  // Hello
                                  // World
                                  // 实际效果等同于 \n

    std::cout << "Hello\40World"; // 输出：Hello World （插入一个空格）

    char str[] = "Hello\0World";
    std::cout << str; // 输出：Hello （由于\0表示字符串结束，World部分不会被输出）

    std::cout << "\115"; // 输出：M

    std::cout << "\x4d"; // 输出：M
    return 0;
}
```

p40_01,

```cpp
#include <iostream>

int main()
{
    std::cout << "Hi \x4dO\115!\n"; // prints Hi MOM! followed by a newline
    std::cout << '\115' << '\n';    // prints M followed by a newline
    return 0;
}
```

p40_02,

```cpp
#include <iostream>

int main()
{
    // 1. L'a' - wide character literal (wchar_t)
    wchar_t wideChar = L'a';
    std::wcout << L"Wide character literal: " << wideChar << std::endl;

    // 2. u8"hi!" - UTF-8 string literal
    const char *utf8String = u8"hi!";
    std::cout << "UTF-8 string literal: " << utf8String << std::endl;

    // 3. 42ULL - unsigned long long literal
    unsigned long long ullValue = 42ULL;
    std::cout << "Unsigned long long literal: " << ullValue << std::endl;

    // 4. 1E-3F - single-precision floating-point literal (float)
    float floatValue = 1E-3F;
    std::cout << "Single-precision floating-point literal: " << floatValue << std::endl;

    // 5. 3.14159L - extended-precision floating-point literal (long double)
    long double longDoubleValue = 3.14159L;
    std::cout << "Extended-precision floating-point literal: " << longDoubleValue << std::endl;

    return 0;
}
```

p41,

```cpp
#include <iostream>

int main() {

    bool test = false;
    std::cout << test << std::endl;
    return 0;
}
```


