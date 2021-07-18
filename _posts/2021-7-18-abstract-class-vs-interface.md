---
layout: post
title: Abstract Class vs. Interface in Java
---

An abstract Class is a Class that cannot be instantiated, partly due to the use and inclusion of abstract methods in abstract classes and interfaces alike. For example, if we had an abstract class named Animal, we wouldn't be able to create an Animal object. However, we are able to implement the methods and variables used in the animal class to create subclasses, for example a Turtle subclass that is implemented by the Animal class. The Turtle class would inherit all the methods and variables from the Animal class it inherited from, and we would also need to override the abstract methods we inherited as well (abstract methods are methods without code in their body).

```java
public abstract class Animal {
    
    protected abstract void live();
    protected abstract void breathe();
    protected abstract void eat();
    protected abstract void die();
    
    // Animal class with abstract methods must have abstract in their name.
}
```
```java
public class Turtle extends Animal {

    @Override
    protected void live() {
        // code implementation details on turtle living.
    }

    @Override
    protected void breathe() {
        // code implementation details on turtle breathing.
    }

    @Override
    protected void eat() {
        // code implementation details on turtle eating.
    }

    @Override
    protected void die() {
        // code implementation details on turtle dying.
    }
}
```

In the example code above, we can see that an abstract class is a class that also can use abstract methods. Similar to a class, we are able to change the access modifier (private, public, protected, etc.) and whether methods are static or non - static. However, in interfaces methods are static and are only public or private (added private access modifier in Java 9).

When to use an abstract class: 
1. We want to share methods and/or code among many subclasses (i.e all subclasses have a method to print all methods inside their class).
2. Code reusability (we don't want to type the same code for the same method multiple times).
3. Template for future specific classes.

In an interface, similar to an abstract class, there is the use of abstract methods and the inability to instantiate, rather to only implement the interface elsewhere. Interfaces are different because they can only run abstract and static methods, where abstract classes can run abstract or normal methods, static or non - static, and multiple access modifiers. While having a lack of features looks like a downside, interfaces gain in the ability to inherit from multiple interfaces, whereas abstract classes can only inherit from one abstract class.

```java
public interface Cloner {
    void clone(Clone objectToBeCloned);
}
```
```java
public class TurtleCloner implements Cloner {
    @Override
    public void clone(Clone objectToBeCloned) {
        // turtle cloning implementation code.
    }
}
```
When to use an interface:
1. When we want to acheive abstraction.
2. When a problem needs to be solved by using multiple inheritance
3. When there isn't a specification on the level of implementation (who implements it or how much/little).
