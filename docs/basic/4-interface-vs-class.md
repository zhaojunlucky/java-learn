---
layout: default
nav_order: 4
title: Interface & Class
has_children: false
parent: Java Basic
published: true

---

# What is Interface

Generally speaking, an Interface is a group of related methods. Objects define the interaction with the outside world through the methods that they expose. Any other classes implements the interface have the capabilities described in the interface.

For example, we define a transaction interface like the below,

```java
public interface ITransaction {
    void begin();
    void commit();
    void rollback();
}
```

In the outside world, any database or system implements the interface has transaction capability.



# What is Class

In the object oriented, it has three characters,

* Encapsulation 
  An object can put its data and related operation together, it's an abstract of the object.
  The object can only allow trusted object to operate.

  While outside world has this object, it can manipulate the object by invoking it's method with data.

* Inheritance 
  An object can inherit from another object to have the parent's capabilities. 
  That's to say, the parent shares its data and methods with child. The child can override its parent's methods too.
  The inheritance likes a template design pattern, and in Java multiple inheritance is not allowed.
  Composition is also a kind of "inheritance".

* Polymorphism 
  Allow the object to invoke it's real method implementation during the runtime.

  For example,

  ```java
  public class Animal {
      public abstract void speak();
  }
  
  public class Dog extends Animal {
      public void speak() {
          System.out.println("dog");
      }
  }
  
  public class Bird extends Animal {
      public void speak() {
          System.out.println("bird");
      }
  }
  
  public class World {
      public static void main(String[] args) {
          Animal animal1 = new Dog();
          Animal animal2 = new Bird();
          
          animal1.speak();
          animal2.speak();
      }
  }
  ```

  The above program output is:

  ```plain
  dog
  bird
  ```

  This is because the subclass override the speak method from the parent, allow defines a variable with type `Animal` it will to find the real method to invoke during the runtime.

  > Every object has a virtual method table saves the method reference of the current class, the Java caller will check the object's real type and to find the real method to invoke.

# When to use Interface or Class

See post [When to use Interface or Class](https://blog.magicworldz.de/java/when-to-use-abstract-class-and-interface/).