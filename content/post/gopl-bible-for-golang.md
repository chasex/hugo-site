+++
banner = ""
categories = ["Programming"]
date = "2015-12-30T20:30:00+02:00"
images = []
menu = ""
tags = ["Go"]
title = "GOPL-Go语言编程\"圣经\""

+++

花了一个月的时间，断断续续终于把`The Go Programming Language(GOPL)`看完了。至于
读后感，用一句话来总结，大概就是：”这是一本注定要成为Go语言编程圣经的书。“

<!--more-->

<img src="/images/cover.png" width="400" height="496" title="The Go Programming Language" alt="The Go Programming Language">

全书内容从基本数据类型讲起，过渡到函数、接口等OOP编程相关，然后深入并发控制、通信
与同步等进阶话题，再到构建系统、测试框架，最后以反射、低阶编程等高级话题结束，编排
合理，文笔简练。GOPL基本覆盖到了Go的全貌，对发展历史、语言特性、运行机制等各个方面
都作了深入浅出的阐述。全书提供了大量的代码实例，比官网的交互教程更加深入，比枯燥的
Language Specification更加生动。书中甚至还花了大量的篇幅介绍Go项目管理，如包管理、
构建系统、文档、测试框架(单元测试、代码覆盖率...)、profiling等，这些内容在同类型的
书是比较少见的。

提起本书的两位作者，可谓大有来头。作者之一的Brian Kernighan，曾与Ken Thompson
和Dennis Ritchie同在Bell Labs共事，UNIX的早期贡献者。他是awk发明者之一，还是世界上第一个写出
Hello World程序的人。他与Ritchie合著的`The C Programming Language`，被誉为C语言编程
的"圣经"。另一作者Alan Donovan，是Google的Go开发组成员，参与开发了诸多标准库，以及
多个静态分析工具，如oracle, doc, rename等。再看看本书的审校，Rob Pike和Russ Cox两位Go的设计者，
加上其他核心开发组成员，阵容可谓空前强大。

如果我们追溯一下Go的历史，会发现一个很重要的项目——[Plan 9](http://plan9.bell-labs.com/plan9/)。
这是Rob Pike和Russ Cox在Bell Labs开发的分布式操作系统，它借鉴了UNIX的设计思想，将所有的硬件资源都
抽象成统一的文件形式。通过一个称为9P的网络协议，把许多节点联结成一个集群，并允许各个节点像本地一样调度
全局资源(是不是很像GFS？)。Plan 9项目是一个伟大的构想，它比Google在2006年以后掀起的分布式计算浪潮
整整领先了15年，而且做得更彻底，直接在系统层面实现分布式。但是，这样一个项目，从1992年第一个发布，
到2002年最后一次发布，此后的十几年间再无动静。随着，AT&T公司在2000年左右的动荡，分拆再分拆，Bell Labs
几易其主后逐渐衰微，人才凋零。Plan 9项目也不能幸免，无人开发维护，至今前途未卜，实在令人不胜唏嘘。

Go脱胎于Plan 9项目，用户态线程(goroutine)的设计，非常适合应用于存在大量网络通信的分布式系统。
随着网络的发展，高并发、低延迟、大数据等要求，使得计算机系统逐渐从单机向集群，从集中式向分布式发展。
相信Go以其强静态、高效、并发等诸多优点，未来在各个领域发挥重要作用。
