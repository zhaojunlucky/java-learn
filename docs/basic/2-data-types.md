---
layout: default
nav_order: 2
title: Data Types
has_children: false
parent: Java Basic
published: true

---

# Data Types

## Primitive

Primitive data types are byte, short, int long, float, double, char and boolean. Both of them have a reference type class defined.

| Type    | Native Type | Bytes | Bits | Default | Range                      | Related Reference Class | Reference Class Cache Range | Configurable              |
| ------- | ----------- | ----- | ---- | ------- | -------------------------- | ----------------------- | --------------------------- | ------------------------- |
| byte    | jbyte       | 1     | 8    | 0       | [-128, 127]                | Byte                    | [-128, 127]                 | N                         |
| int     | jint        | 4     | 32   | 0       | [$-2^{-32}$, $2^{32}-1$]   | Integer                 | [-128, 127]                 | Y `-XX:AutoBoxCacheMax=N` |
| float   | jfloat      | 4     | 32   | 0f      |                            | Float                   |                             |                           |
| double  | jdouble     | 8     | 64   | 0d      |                            | Double                  |                             |                           |
| char    | jchar       | 2     | u16  | 'u0000' |                            | Character               | [0, 127]                    | N                         |
| boolean | jboolean    | 1     | u8   | false   |                            | Boolean                 | [false, true]               | N                         |
| short   | jshort      | 2     | 16   | 0       | [$-2^{16}$,  $2^{16}-1$]   | Short                   |                             |                           |
| long    | jlong       | 8     | 64   | 0l      | [$-2^{64}$,  $2^{64} - 1$] | Long                    |                             |                           |
| void    | void        |       | N/A  | N/A     |                            | Void                    |                             |                           |

## Reference

* Class
* Interface
* Array Class
* Generic（Generic Parameter will be eased during the compile）

## Pass by value OR Pass by reference 

### Primitive Type

Take the following code as an example,

```java
public class Main {
    private static void test(int a) {
        System.out.println(a);
        // try to modify a 
        a = 1000;
    }
    
    public static void main(String[] args) {
        int a = 10;
        test(a);
        System.out.println(a);
    }
}

The output:
10
10
```

From the result we can see it pass the variable by "value".

* in method `main` the variable `a` is allocated in stack
* when pass to the method `test`, the `a` is copied, so when change the value of a in method `test`, it will not change the value in `main`

### Reference Type

Take the following code as an example,

```java
public class Main {
    private static void test1(AtomicInteger a1) {
        System.out.println(a1.get());
        // try to modify a1 
        a1 = new AtomicInteger(10000);
    }
    
    private static void test2(AtomicInteger a2) {
        // try to modify a2
        a2.set(1000);
    }
    
    public static void main(String[] args) {
        AtomicInteger a = new AtomicInteger(10);
        test1(a);
        System.out.println(a.get());
        
        test2(a);
        System.out.println(a.get());
    }
}

The output:
10
10
1000
```

From the result we can see the it doesn't pass the variable by reference.

* `a` is a variable allocated in stack reference to a heap memory which stores the value `10`
* when pass to method `test1`, it tries to assign a new variable to the passed variable `a1`, but the origin `a` is not changed
  This is because a copied `a` which is `a1` passed to method `test1`, we changed the reference of `a1` to a new memory address, but no effect to the origin referenced memory
* when pass to method `test2`, it tries to set a new value for the origin object, so in main method prints the new value.
  Although the `a2` is a copied variable, it has the same reference memory, so the changes reflect in main.

