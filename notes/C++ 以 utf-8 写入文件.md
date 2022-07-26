---
title: C++ 以 utf-8 写入文件
created: '2022-07-25T05:25:57.256Z'
modified: '2022-07-25T05:29:41.223Z'
---

# C++ 以 utf-8 写入文件

## 编码转换

```cpp
#include <cstdio>
#include <codecvt>

int main() {
    std::wstring_convert<std::codecvt_utf8_utf16<wchar_t>,wchar_t> convert;
    std::string utf8_string = convert.to_bytes(L"кошка 日本国");

    if(FILE *f = fopen("tmp","w"))
    fprintf(f,"%s\n",utf8_string.c_str());
}
```

## C++ wchar_t 汉字乱码问题

中文字在C/C++中的处理

        如今编程的语言和编程环境随着中国的发展开始对中文有进一步的支持，但是对中文的支持总体来说是有缺陷的，而且有与编译环境的不同导致中文在当前的C/C++中有很多问题，而且很多版本对中文的支持是不完全的，就拿DEV-C++和VS2005为例，对与MSDN的帮助和网上的讲述两者在那些代码的支持有很多不同的地方。

       而我要讨论的就是对于中文在C/C++的应用方法。

首先中文字是在一般char的范围以外的，所以我们不能用单个char存储我们的中文字，于是我们大多引进wchar_t这种宽字符的数据类型。但是在我所用过的编译环境中一般是定义为wchar_t，这是C++语言中认可的定义，他的空间就和unsigned short的大小一样，所以有这样的内部定义：typedef unsigned short wchar_t，他是16位的。

在DEV-C++中我们有很多方法是不能用的，对于VS2005，我们可以定义和应用的很多方法和和很多库函数在DEV-C++都不可以用的。如在MSDN和很多网络资料中提到的输入和输出方法像wcin和wout在DEV-C++都是显示未定义的，也就是说DEV-C++是不支持这些方法的。简单宽字符的输入和输出如下：

```cpp
#include<iostream>
using namespace std;
int main()
{
        wchar_t a[3];
        wcin >> a;
        wcout << a << endl;
    return 0;
}
```

       但这样只能输入单个汉字字符,如果超过2个中文字就会有溢出的错误，而用这样的方法，虽然我们用了wchar但完全没有突出我们的目的，它仍然是一个中文字占两个wchar_t单位，而且我们也没有办法对里面的汉字字符进行操作所以这是不可行的，但这是C的用法，在C++中wchar则对其进行了修改，使得中文的支持更加好了。

      在C++中，wchar_t是语言内建的数据类型，wchar_t的长度是由实现决定的。现在我们正式开始讨论中文在我们的C++中的支持和应用的问题。

       C++是一种很好的语言，它为了适合不同的地域语言的开发，它加入了一个叫做locale包的头文件，里面定义了不同语言和语言的缩写。这是我们使用wchar_t进行中文的个方面的操作的一个重要的环节。对于我们的输入输出有很重要的影响。

```cpp
#include <iostream>
#include <locale>
using namespace std;

int main()
{
    locale loc("Chinese-simplified");
    wcin.imbue(loc);
    wcout.imbue(loc);
    //上面三行代码和setlocale(LC_ALL,"chs");作用是一样的。

    wchar_t c[4];
    wcin >> c;
    wcout << c <<endl;
    return 0;
}
```
