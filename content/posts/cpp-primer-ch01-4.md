+++
title = 'C++ Primer 第五版 1.4 控制流 笔记'
date = 2024-09-09T17:53:50+08:00
categories = []
tags = ["C++ Primer", "Bilibili", "C++", "技术", "读书笔记"]
+++

这一集视频我们主要来看一下 C++ Primer 1.4 节。

主要是对几个常用的控制流的语句进行说明，包括，

- while 循环
- for 循环
- 读取输入
- if 语句

我们这里的讲解主要是对书上示例的代码进行相应的解析，对于大家容易理解的知识点，就不去花费多余的时间来说明。删繁就简，同时，不漏疑难点。

## Part1 while 循环

首先是 while 语句，核心是理解这样一句话，

> while **语句**反复执行一段代码，直至给定条件为假为止。

直接看书中的示例代码，

```cpp
#include <iostream>
int main()
{
    int sum = 0, val = 1;
    // keep executing the while as long as val is less than or equal to 10
    while (val <= 10)
    {
        sum += val; // assigns sum + val to sum
        ++val;      // add 1 to val
    }
    std::cout << "Sum of 1 to 10 inclusive is " << sum << std::endl;
    return 0;
}
```

## Part2 for 循环

然后是 for 语句，我们更加常用的一种循环语句，

比如，书上的例子是从 1 加到 10，

```cpp
#include <iostream>
int main()
{
    int sum = 0;
    // sum values from1 through 10 inclusive
    for (int val = 1; val <= 10; ++val)
        sum += val; // equivalent to sum = sum + val
    std::cout << "Sum of 1 to 10 inclusive is " << sum << std::endl;
    return 0;
}
```

for 循环后面如果不加花括号，那么，for 循环中只会执行一条语句，

```cpp
#include <iostream>
int main() {
    int sum = 0;
    // sum values from1 through 10 inclusive
    for (int val = 1; val <= 10; ++val) 
        sum += val;  // equivalent to sum = sum + val
        sum += 100; 
    std::cout << "Sum of 1 to 10 inclusive is " << sum << std::endl;
    return 0;
}
// output: 155
```

我们再来看加了花括号的效果，

```cpp
#include <iostream>
int main() {
    int sum = 0;
    // sum values from1 through 10 inclusive
    for (int val = 1; val <= 10; ++val) {
        sum += val;  // equivalent to sum = sum + val
        sum += 100; 
    }
    std::cout << "Sum of 1 to 10 inclusive is " << sum << std::endl;
    return 0;
}
// output: 1055
```

## Part3 读取输入

读取输入数据。

```cpp
#include <iostream>
int main()
{
    int sum = 0, value = 0;
    // read until end-of-file, calculating a running total of all values read
    while (std::cin >> value)
        sum += value; // equivalent to sum = sum + value
    std::cout << "Sum is: " << sum << std::endl;
    return 0;
}
```

从键盘输入文件结束符(EOF, end of file)这里，书上说的是在 Windows 下，输入文件结束符的方法是敲 Ctrl + Z，然后按回车键，但是在上面这个程序中无法体现，因为我们只要输入的不是一个 int 值，循环就会结束，比如，我们输入 Ctrl + D 然后回车也是可以的。所以，我们可以单独写一个程序来验证一下这个文件结束符，

```cpp
// 测试一下 Windows 下 Ctrl + Z 然后回车是否是 EOF
#include <cstdio>
#include <iostream>

int main()
{
    int x;
    if ((x = std::cin.get()) == EOF)
    {
        std::cout << "Here is an EOF." << std::endl;
    }
    return 0;
}
```

同时，这一小节中，书上还介绍了编写程序时会导致的一些编译错误，这里具体演示一下，

- 语法错误
- 类型错误
- 声明错误

首先是语法错误，

```cpp

```

然后是类型错误，比如，

```cpp
int a = "this is a string";
```

然后是声明错误，

```cpp
#include <iostream>
int main()
{
    int v1 = 0, v2 = 0;
    std::cin >> v >> v2; // error: uses "v" not "v1"
    // error: cout not defined; should be std::cout
    cout << v1 + v2 << std::endl;
    return 0;
}
```

## Part4 if

```cpp
#include <iostream>
int main()
{
    // currVal is the number we’re counting; we’ll read new values into val
    int currVal = 0, val = 0;
    // read first number and ensure that we have data to process
    if (std::cin >> currVal)
    {
        int cnt = 1; // store the count for the current value we’re processing
        while (std::cin >> val)
        {                       // read the remaining numbers
            if (val == currVal) // if the values are the same
                ++cnt;          // add 1 to cnt
            else
            { // otherwise, print the count for the previous value
                std::cout << currVal << " occurs " << cnt << " times" << std::endl;
                currVal = val; // remember the new value
                cnt = 1;       // reset the counter
            }
        } // while loop ends here
        // remember to print the count for the last value in the file
        std::cout << currVal << " occurs " << cnt << " times" << std::endl;
    } // outermost if statement ends here
    return 0;
}
// input: 42 42 42 42 42 55 55 62 100 100 100
```


