---
layout: default
title: Java Basic
nav_order: "2"
has_children: true
permalink: "/docs/basic"

---
# Java Basic

Java is a write once, runs every language, but also it's a great platform which has a good mature ecosystem. That allows us to design and develop an application or product with many existing components and library. But also, after about 20 years developments, Java, in  some word, it become a bloated platform, compared with other new language such as golang. 

One example, is that when I write a simple customize http proxy with golang, it's very lightweight with zero dependence, but with Java, I need to setup Spring/Spring boot, that turns the project become much complicated. 

Beside this, I do think Java is good language and it's popular in many industry areas.

## Basic Characters

Java or Java platform have some features which different with C/C++, for example.

* GC  
  In C/C++, we need to manually mange the memory, and we may get memory leak, illegal pointer during the application runtime, which is painful for many of the beginners.  
  And I also remember when I started to write the C program in the Linux, I was confused, mad and anxious with the segment fault during that time.

  But with Java, I don't need to manually free the memory, that free the developers a lot, put us focusing on the business. 

  > Actually, there is till memory leak in Java application, but that's different with C/C++.

  However, despite the GC brings developer a lot a benefits there is also some bad effects. 
  * The GC may degrade the performance, if the application is not well designed
  * The operation may take more time to do the GC performance tuning.
  * During the GC, it will do stop the world in a short time
  * The GC may cause the memory fragmentation
  * As GC will maintain a data structure, it will consume more memory
* Pure Object Oriented

  Java is a pure object oriented language, that to say, a class is required even if we write a hello world program.  
  In the good aspect, it makes sure everyone who writes the code must follow the Java standard, which can set the lower limit.  
  But in the other hand, it also makes the code become wordy, doctrine.  
  However, Java also evolve many new features such as lambda, interface default methods and stream. 
* Static Compile  
  This is the same like other languages such as C/C++, golang. I really like static compile language, which can avoid many compile time errors. That's why a always prefer Java, Golang that python.

## Java Platform Overview

TBD