---
layout: default
nav_order: 5
title: Class Loader
has_children: false
parent: Java Basic
published: true

---

# What Is Class Loader

Class loader is used to load, link and resolve a class into the memory to execute.

In Java, there are 3 default class loaders provided by the JVM,

* Bootstrap class loader
  Load classes under module`java.base`. So, any classes loaded by this class loader's class loader is null

* Platform class loader
  Any other modules except `java.base`

  > Below Java 9, it's called ext class loader, and start from Java 9, extension mechanism is removed.

* Application class loader
  User classes.

For example,

```java
import java.net.http.HttpClient;

public class ClassLoaderTest {
    public static void main(String[] args) {
        System.out.println("String->" + String.class.getClassLoader());
        System.out.println("HttpClient->" + HttpClient.class.getClassLoader());
        System.out.println("ClassLoaderTest->" + ClassLoaderTest.class.getClassLoader());
    }
}

```

Run the above program will get output like the below.

```plain
String->null
HttpClient->jdk.internal.loader.ClassLoaders$PlatformClassLoader@1698c449
ClassLoaderTest->jdk.internal.loader.ClassLoaders$AppClassLoader@2f0e140b
```

## Parent-delegation

When a class loader load a class, it always tries to find the class from the parent first.

* If parent find the class, then return
* Otherwise, trying to find in other location

So, any customize class loader should also follow this rule.

## Class Load Process

### Load

Loading is the process of finding the binary representation of a class or interface type with a particular name and creating a class or interface from that binary representation.

### Linking

Linking is the process of taking a class or interface and combining it into the run-time state of the Java Virtual Machine so that it can be executed.

Linking a class or interface involves verifying and preparing that class or interface, its direct superclass, its direct superinterfaces, and its element type (if it is an array type), if necessary. Resolution of symbolic references in the class or interface is an optional part of linking.

This specification allows an implementation flexibility as to when linking activities (and, because of recursion, loading) take place, provided that all of the following properties are maintained:

- A class or interface is completely loaded before it is linked.
- A class or interface is completely verified and prepared before it is initialized.
- Errors detected during linkage are thrown at a point in the program where some action is taken by the program that might, directly or indirectly, require linkage to the class or interface involved in the error.

#### Verification

Verification ensures that the binary representation of a class or interface is structurally correct. Verification may cause additional classes and interfaces to be loaded but need not cause them to be verified or prepared.

* If the binary representation of a class or interface does not satisfy the static or structural constraints, then a VerifyError must be thrown at the point in the program that caused the class or interface to be verified.

* If an attempt by the Java Virtual Machine to verify a class or interface fails because an error is thrown that is an instance of LinkageError (or a subclass), then subsequent attempts to verify the class or interface always fail with the same error that was thrown as a result of the initial verification attempt.

#### Preparation

Preparation involves creating the static fields for a class or interface and initializing such fields to their default values. This does not require the execution of any Java Virtual Machine code; explicit initializers for static fields are executed as part of initialization, not preparation.

#### Resolution

*Resolution* is the process of dynamically determining concrete values from symbolic references in the run-time constant pool.

Resolve the symbolic reference to concrete reference. If a symbolic reference is an unloaded class, or the field or method, it will trigger to the load of this class.

> Cause load of the reference class may not do linking and initializing

### Initializing

Initialization of a class or interface consists of executing the class or interface initialization method `<clinit>`

A class or interface may be initialized only as a result of:

- The execution of any one of the Java Virtual Machine instructions *new*, *getstatic*, *putstatic*, or *invokestatic* that references the class or interface (*new*, *getstatic*, *putstatic*, *invokestatic*). All of these instructions reference a class directly or indirectly through either a field reference or a method reference.

  Upon execution of a *new* instruction, the referenced class or interface is initialized if it has not been initialized already.

  Upon execution of a *getstatic*, *putstatic*, or *invokestatic* instruction, the class or interface that declared the resolved field or method is initialized if it has not been initialized already.

- The first invocation of a `java.lang.invoke.MethodHandle` instance which was the result of resolution of a method handle by the Java Virtual Machine and which has a kind of 2 (`REF_getStatic`), 4 (`REF_putStatic`), or 6 (`REF_invokeStatic`).

- Invocation of certain reflective methods in the class library, for example, in class `Class` or in package `java.lang.reflect`.

- The initialization of one of its subclasses.

- Its designation as the initial class at Java Virtual Machine start-up.

Prior to initialization, a class or interface must be linked, that is, verified, prepared, and optionally resolved.

> Refer to office introduction https://docs.oracle.com/javase/specs/jvms/se7/html/jvms-5.html#jvms-5.4.3

