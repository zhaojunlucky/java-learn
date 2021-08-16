---
layout: default
title: Java Basic
nav_order: "2"
has_children: true
permalink: "/docs/basic"

---
# Java Basic

Java is a write-once, runs every language, but also it's a great platform that has a good mature ecosystem. That allows us to design and develop an application or product with many existing components and libraries. But also, after about 20 years of development, Java, in some words, it becomes a bloated platform, compared with other new languages such as Golang.

One example is that when I write a simple customize HTTP proxy with Golang, it's very lightweight with zero external dependence, but with Java, I need to set up Spring/Spring boot, which turns the project become much complicated.

Besides this, I do think Java is a good language and it's popular in many industry areas.

## Basic Characters

Java or Java platforms have some features which differ from other languages, for example.

* GC  
  In C/C++, we need to manually manage the memory, and we may get memory leaks, illegal pointers during the application runtime, which is painful for many beginners.  
  And I also remember when I started to write the C program in Linux, I was confused, mad, and anxious about the segment fault during that time.

  But with Java, I don't need to manually free the memory, that frees the developers a lot, put us focusing on the business.

  > Actually, there is till memory leak in Java application, but that's different with C/C++.

  However, despite the GC brings developers a lot of benefits there are also some bad effects.
  * The GC may degrade the performance if the application is not well designed
  * The operation may take more time to do the GC performance tuning.
  * During the GC, it will do stop the world in a short time
  * The GC may cause the memory fragmentation
  * As GC will maintain a data structure, it will consume more memory
* Pure Object-Oriented

  Java is a pure object-oriented language, that to say, a class is required even if we write a hello world program.  
  In the good aspect, it makes sure everyone who writes the code must follow the Java standard, which can set the lower limit.  
  But on the other hand, it also makes the code become wordy, doctrine.  
  However, Java also evolves many new features such as lambda, interface default methods, and stream.
* Static Compile  
  This is the same as other languages such as C/C++, Golang. I really like static compile language, which can avoid any compile-time errors. That's why a always prefer Java, Golang that python.

## Java Platform Overview

### Language features

1. Object-Oriented
2. Reflection
3. Generic

### Built-In Libraries

1. Core Libraries
   * IO/NIO
   * Network
   * ThreadPool, Executors
   * Collection, Collection Utils
2. Security Libraries
3. jdk.management
4. Third-party

### JVM

1. GC
2. Runtime
3. JIT
4. Accessibility
   * JFR

### Java Ecosystems

1. Spring/Spring Boot
2. Hadoop
3. Kafka
4. ElasticSearch
5. Maven
6. Gradle

### Tools

1. Accessibility: jlink, jar, jdeps
2. Compiler: javac, sjavac
3. Diagnostic: jmap, jps, jstack, jconsole, jcmd, jhsdb, visual vm