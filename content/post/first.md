+++
categories = ["Lorem"]
date = "2015-12-15T13:50:46+02:00"
menu = ""
tags = ["Golang"]
title = "这是我的第一篇博客"
+++

## 测试
代码高亮

Go

~~~C
import "fmt"
import "github.com/chasex/test"

func main() {
    var s string
    slice := []int{1, 2, 3}
    for _, i := range slice {
        fmt.Println(i)    
    }
}
~~~

C

~~~C
#include <stdio.h>

int main() {
    // This is a test program
    printf("hello world");    
    return 0;
}
~~~

C++

~~~C++
#include <iostream>
#include <string>

int main () {
    std::string str;
    std::string base="The quick brown fox jumps over a lazy dog.";

    // used in the same order as described above:

    str.assign(base);
    std::cout << str << '\n';

    str.assign(base,10,9);
    std::cout << str << '\n';         // "brown fox"
    return 0;
}
~~~
图片
![测试1](/banners/placeholder.png)
![测试2](/banners/home-bg.jpg)
