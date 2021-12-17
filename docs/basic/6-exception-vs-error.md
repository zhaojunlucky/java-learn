---
layout: default
nav_order: "6"
title: Exception & Error
has_children: false
parent: Java Basic
published: false

---
# What are Exception and Error

In the Java world, there are exceptions and errors that can be thrown by the running JVM, they are similar, but they are actually different.

* Both of them inherits from the `Throwable`. In Java, only `Throwable` can be thrown and caught, it is the basic mechanism in Java exception handling.
* The exception is expected during the application runtime, and it can and should be caught for processing. This is a possible code execution route.
  * An Exception can be a checked exception or an unchecked exception. The checked exception must be explicitly caught, throws in the application code, it is a compile-time check. The unchecked exception is a kind of `RuntimeException` , such as `NullpointerException` and `ArrayIndexOutOfBoundsException`. They usually are a logic error that can be avoided, and they can be caught on demand and are not enforced at the runtime.
* However, Error is a kind of abnormal state that should not happen, once it happened, it will cause the application in an abnormal or unrecoverable state. It should not be caught by the application code, such as `OutOfMemoryError` or `ClassNotFoundError`.

# How to Catch the Exception

## Exception Class Diagram in Java

![](/uploads/exception-class.webp)

### NoClassDefFoundError Example

1. Source code

   ```java
   public class A {
       public static void main(String[]args) {
        var b = new B();
      }
   
   static class B {
   }
   }
   ```

2. Compile A.java

   ```bash
   > javac A.java
   ```

   Will get two compiled class.

   ```bash
   A.class
   A$B.class
   ```

3. Remove compiled class `A$B.class`, then run `java A`, will got `NoClassDefFoundError`
   
   ```bash
   > java A
   Exception in thread "main" java.lang.NoClassDefFoundError: A$B
           at A.main(A.java:3)
   Caused by: java.lang.ClassNotFoundException: A$B
           at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:641)
           at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:188)
           at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:520)
           ... 1 more
   ```
   
   

### ClassNotFoundException Example

Run the following source code will get `ClassNotFoundException`.

```java
public class A {
    public static void main(String[]args) throws ClassNotFoundException {
     Class.forName("B");
   }

}


```

Run with `java A.java`.

```bash
> java A.java
Exception in thread "main" java.lang.ClassNotFoundException: B
        at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:641)
        at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:188)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:520)
        at jdk.compiler/com.sun.tools.javac.launcher.Main$MemoryClassLoader.loadClass(Main.java:600)
        at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:520)
        at java.base/java.lang.Class.forName0(Native Method)
        at java.base/java.lang.Class.forName(Class.java:375)
        at A.main(A.java:3)
```



## Example to Throw or Catch Exception

```java
public ExceptionTest {
  // explicitly handle the checked exception
  public void readFile(String file) throws FileNotFoundException {
    // read file
  } 
  
  public static void main(String[] args) {
    
  }
}
```

