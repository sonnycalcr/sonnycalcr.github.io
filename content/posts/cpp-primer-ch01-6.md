+++
title = 'C++ Primer 第五版 1.6 书店程序 笔记'
date = 2024-09-11T20:31:29+08:00
categories = []
tags = ["C++ Primer", "Bilibili", "C++", "技术", "读书笔记"]
+++

本节主要的内容只有一份代码，就是标题所说的书店程序，

```cpp
#include <iostream>
#include "Sales_item.h"
int main()
{
    Sales_item total; // variable to hold data for the next transaction
    // read the first transaction and ensure that there are data to process
    if (std::cin >> total)
    {
        Sales_item trans; // variable to hold the running sum
        // read and process the remaining transactions
        while (std::cin >> trans)
        {
            // if we’re still processing the same book
            if (total.isbn() == trans.isbn())
                total += trans; // update the running total
            else
            {
                // print results for the previous book
                std::cout << total << std::endl;
                total = trans; // total now refers to the next book
            }
        }
        std::cout << total << std::endl; // print the last transaction
    }
    else
    {
        // no input! warn the user
        std::cerr << "No data?!" << std::endl;
        return -1; // indicate failure
    }
    return 0;
}

/* input:
0-201-70353-X 4 24.99
0-201-82470-1 4 45.39
0-201-88954-4 2 15.00
0-201-88954-4 5 12.00
0-201-88954-4 7 12.00
0-201-88954-4 2 12.00
0-399-82477-1 2 45.39
0-399-82477-1 3 45.39
0-201-78345-X 3 20.00
0-201-78345-X 2 25.00
*/
```

可能有同志会注意到这个程序在读取输入的时候，最后可能需要先回车一下，然后按下 Ctrl + Z 然后再回车，才能使程序接收到 EOF(end of file) 信号，这个[问题](https://stackoverflow.com/questions/31261483/why-ctrl-z-does-not-trigger-eof)我们只需要知道如何去规避即可，如果想刨根究底，那么，也没有问题，推荐去看以下两个链接，主要是第二个链接，

- <https://stackoverflow.com/questions/1782080/what-is-eof-in-the-c-programming-language>
- <https://stackoverflow.com/questions/5655112/why-do-i-require-multiple-eof-ctrlz-characters>


