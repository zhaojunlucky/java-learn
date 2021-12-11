---
layout: default
nav_order: 6
title: Exception & Error
has_children: false
parent: Java Basic
published: false

---

# What is Exception and Error

In the Java world, there are exception and errro that can be throw by the running JVM, they are similar, but they are actually different.

* Both of them inherits from the `Throwable`. In Java, only `Throwable` can be throw and catch, it is the basic mechianism in Java exception handling.

* Exception is expected during the application runtime, and it can and should be catched for processing. This is a possible code execution route.

  * An Exception can be a checked exception or an unchecked exception. The checked exception must be explict catched, throws in the appliction code, it is a compile-time check. The unchecked exception is a kind of `RuntimeException` , such as `NullpointerException` and `ArrayIndexOutOfBoundsException`. They usaually are logic error which can be avoid, and they can be catched on demand, and is not enforced at the runtime.

* However, Error is a kind a abnormal state that should not happen, once it happend, it will cause the application in a abnomal or uncoveryable state. It should not catched by the application code, such as `OutOfMemoryError` or `ClassNotFoundError`.

  

# The Exception Class Design

