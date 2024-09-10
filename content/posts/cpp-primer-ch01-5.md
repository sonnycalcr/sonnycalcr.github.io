+++
title = 'C++ Primer 第五版 1.5 类简介 笔记'
date = 2024-09-10T21:00:20+08:00
categories = []
tags = ["C++ Primer", "Bilibili", "C++", "技术", "读书笔记"]
+++

这一集我们简要介绍一下类这个知识点。

所谓的类，我们可以把它想象成一个内置的类型一样的物件，然后，和内置类型不同的点在于，类需要我们自己去设计和定义。

这一小节主要是让我们看一下如何简单地使用一个类。

## Part1 Sales_item 类

那么，接下来接直接看代码，看一下如何简单地使用 Sales_item 这个类，

```cpp
#include <iostream>
#include "Sales_item.h"

int main() 
{
    Sales_item book;

    // read ISBN, number of copies sold, and sales price
    std::cin >> book;
    // write ISBN, number of copies sold, total revenue, and average price
    std::cout << book << std::endl;

    return 0;
}
```

这里插一句，书中的代码也可以直接到配套网站去下载，

<https://www.informit.com/store/c-plus-plus-primer-9780321714114>

书上有些没有给出的代码，但是配套代码给出了，那么，对于这一部分，我们就去到配套代码那里给取过来。比如，我们这里的代码想要跑通，就得把 Sales_item.h 这个头文件给复制过来。

然后，是第二份代码，

```cpp
#include <iostream>
#include "Sales_item.h"
int main()
{
    Sales_item item1, item2;
    std::cin >> item1 >> item2;              // read a pair of transactions
    std::cout << item1 + item2 << std::endl; // print their sum
    return 0;
}
```

按：关于书上提到的重定向操作，在 Windows 的命令行提示符和 Linux 系统的 shell 中，确实可以像下面这样，

```shell
addItems < infile > outfile
```

但是，在 PowerShell 中，我们得用另一种语法，

```shell
Get-Content .\input.txt | addItems.exe > .\output.txt
```

## Part2 成员函数

然后，是成员函数的简单使用，

```cpp
#include <iostream>
#include "Sales_item.h"
int main()
{
    Sales_item item1, item2;
    std::cin >> item1 >> item2;
    // first check that item1 and item2 represent the same book
    if (item1.isbn() == item2.isbn())
    {
        std::cout << item1 + item2 << std::endl;
        return 0; // indicate success
    }
    else
    {
        std::cerr << "Data must refer to same ISBN" << std::endl;
        return -1; // indicate failure
    }
}
}
```


