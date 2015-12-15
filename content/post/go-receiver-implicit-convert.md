+++
date = "2015-12-02T22:45:43+02:00"
title = "Go Receiver的隐式转化"
tags = ["Go"]
images = []
categories = ["Programming"]
+++

最近在读`The Go Programming Language`，第6章提到了method receiver的隐式转化。
这是初学Go比较令人困惑的地方，之前做项目也有犯类似错误，故在此归纳记录一下。

在Go中method的receiver要么是自定义类型，要么是指向自定义类型的指针。
~~~C
type Point struct {
    X, Y float64
}

func (p Point) Distance() float64 {
    return math.Hypot(p.X, p.Y)    
}

func (p *Point) Scale(factor float64) {
    p.X *= factor    
    p.Y *= factor
}
~~~

Go允许T类型的变量调用receiver为\*T的方法，编译器隐式地对变量做了取地址操作。
同样地，也允许\*T类型的变量调用receiver为T的方法，编译器隐式地对指针做了解引用操作。
这是一个很好用的语法糖，使得我们在编码时不用做显式类型转化。
但是要注意，对于临时变量，由于无法获取地址，Go不会做隐式的转化。
~~~C
func main() {
    p := Point{3, 4}

    p.Distance()
    p.Scale(2)          // implicit (&p)
    fmt.Println(p)      // {6, 8}

    q := &Point{3, 4}
    q.Distance()        // implicit (*q)
    q.Scale(2)          
    fmt.Println(q)      // &{6, 8}
    
    Point{3, 4}.Scale(2) // compile error
}
~~~

那么这种转化是否适用于interface呢？让我们来看一个例子。
~~~C
type Interface interface {
    String() string
    Set(s string)
}

type Message struct {
    msg string
}

func (s Message) String() string {
    return "Message: " + s.msg
}

func (s *Message) Set(msg string) {
    s.msg = msg
}

func main() {
    m1 := Message{"hello world"}
    m2 := &Message{"hello world"}

    m1.String()
    m1.Set("new message")

    m2.String()
    m2.Set("new message")

    fmt.Println(m1)
    fmt.Println(m2)

    var _ Interface = m1    // compile error
    var _ Interface = m2
}
~~~

在这个例子中，为Message定义了一个String方法，为\*Message类型定义了一个Set方法。
Message类型的变量m1能调用String和Set方法，但是不满足Interface接口，编译器提示
Set方法缺失。反之，\*Message类型的变量m2既能调用String和Set方法，同时也满足
Interface接口。

可见，T类型不会自动拥有以\*T作为receiver的方法，而\*T类型却会自动拥有以T作为recevier
的所有方法。这该如何理解呢？其实很好理解，当一个方法以\*T作为receiver时，
这个方法可能会改变变量的值。如果将它应用于T，改变的只是变量的副本，
而对原值没有影响，从而造成非预期结果。当一个方法以T作为receiver时，我们预期它不会改变变量的值，将它应用于\*T也不会有任何负面影响，因此编译器会为我们自动生成一个以\*T作为receiver的版本。
