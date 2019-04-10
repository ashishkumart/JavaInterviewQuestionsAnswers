# JavaInterviewQuestionsAnswers
Core Java Interview questions and answers

## General
 **1. What is the latest version of Java SE?**
 
Java SE 12 (March 2019).

**2. What is Annotation?**

Annotations are tags that we can enter in our program code, for some tool to process it, and make sence of it.
1) Annotation starts with `@`
2) Annotation do not change the action of compiled program.
3) Annotations can change the way a program is teated by compiler 

There are three categories of Annotations
1) Marker Annotations: like `@Override`
2) Single value annotations: 
3) Full Annotations

**3. What is reflection?**

Java reflection makes it possible to inspect classes, interfaces, fields, and methods at runtime, without knowing the names of clesses, methods etc. at compile time.
It is also possible to instantiate new objects and get/set the values using reflection.

**4. What is String interning?**

String Interning is a method of storing only one copy of each distinct String value, which must be immutable.

**5. What is difference between Serializable and Externalizable interface?**

1) Serializable is a marker interface which doesnot have any method, whereas Externalizable interface contains two methods readExternal() and writeExternal().
2) Serializable uses reflection to construct object and does not require no-args constructor, whereas Externalizable requires public no-args constructor.

**6. What is volatile?**

Volatile keyword makes sure that the changes made in one thread are immediately reflect in other thread.

`class SharedObj
{
   static volatile int sharedVar = 6;
}`

Note that volatile should not be confused with static modifier. static variables are class members that are shared among all objects. There is only one copy of them in main memory.


**7. What is static variable, class and method?**

###### Static Variable
If a field is declared static, then exactly a single copy of that field is created and shared among all instances of that class.
It doesn’t matter how many times we initialize a class; there will always be only one copy of static field belonging to it. The value of this static field will be shared across all object of the class
From the memory perspective, static variables go in a particular pool in JVM memory called **Metaspace**.

When we should use static field?
*When the value of variable is independent of objects
*When the value is supposed to be shared across all objects.

###### Static method
Static methods are generally used to perform an operation that is not dependent upon instance creation.
If there is a code that is supposed to be shared across all instances of that class, then write that code in a static method.
static methods are also widely used to create utility or helper classes so that they can be obtained without creating a new object of these classes.

- static methods in Java are resolved at compile time. Since method overriding is part of Runtime Polymorphism, so static methods can’t be overridden
- abstract methods can’t be static
- static methods cannot use this or super keywords

The following combinations of the instance, class methods and variables are valid:
 1 -Instance methods can directly access both instance methods and instance variables
 2 -Instance methods can also access static variables and static methods directly
 3 -static methods can access all static variables and other static methods
 4 -static methods cannot access instance variables and instance methods directly; they need some object reference to do so.

###### Static class
Static classes are basically a way of grouping classes together in Java. Java doesn't allow you to create top-level static classes; only nested (inner) static classes.

Reasons to use static inner class

1. Grouping classes that will be used only in one place increases encapsulation.
2. The code is brought closer to the place that will be only one to use it; this increases readability and code is more maintainable.
3. If nested class doesn’t require any access to it’s enclosing class instance members, then it’s better to declare it as static because this way, it won’t be coupled to the outer class and hence will be more optimal as they won’t require any heap or stack memory.
4. Static nested classes do not have access to any instance members of the enclosing outer class; it can only access them through an object’s reference.
5. Static nested classes can access all static members of the enclosing class, including private ones.
6. Java programming specification doesn’t allow us to declare the top-level class as static; only classes within the classes (nested classes) can be made as static.

**8. What is static block? When does this get executed?**

A static block is used for initializing static variables. Although static variables can be initialized directly during declaration, there are situations when we’re required to do the multiline processing.
In such cases, static blocks come in handy. If static variables require additional, multi-statement logic while initialization, then a static block can be used.

1. A class can have multiple static blocks
2. Static fields and static blocks are resolved and executed in the same order as they are present in the class
3. Static block is executed when the class is loaded

**9. What is init block?When does this get executed?**


**10. What is thread interning?**


**11. What is difference between Annoymous Inner Class and Lambda Exp.?**


**12. What are the checked and unchecked exceptions?**


**13. What is the difference between exception and error?**


**14. What is dependecy injection?**


**15. What is HashCode?**


## String
**1. What is String interning?**


**2. What is String pool?**

## Multithreading
**1. What is thread interning?**


**2. What is the lifecycle of a thread?**


**3. What is yield() method?**


**4. What is difference between process and thread?**


**5. What is join() method?**


**6. What is difference between wait() and sleep() method?**


**7. What is difference between wait() and join() method?**

**8. What is thread scheduler?**


**9. What is thread scheduler?**

###### 10. What is Looper?
###### 11. Why the notify() and notifyAll() methods are part of Object class instead of Thread classh?
###### 12. What is thread pool?
###### 13. What is difference betweeen == operator and equals() method?
###### 14. What is Autoboxing and Unboxing?
###### 15. What is the differenve between Comparable and Comparator?
###### 16. What are the synchronous and asynchronous?

## Object Oriented Programming
###### 1. What is thread interning?
###### 2. What is encapsulation?
###### 3. What is polumorphism?
###### 4. What is compile time and runtime polymorphism?
###### 5. Why return type does not play role in method overloading?
###### 6. What is upcasting in Java?
###### 7. What is default method in Java?
###### 8. What is difference between interface and abstract class(after Java 8)?
###### 9. What is difference between default method and static method?
###### 10. What is Enum in Java?
###### 11. What is Generics?
###### 12. What are the interfaces that are implemented in String class?
###### 13. Can we create objetc of interface and abstract class?
###### 14. What is Constructor chaning?


## Java Features
###### 1. What are the features of Java 8?
###### 2. What are the features of Java 12?

## Java Collection
###### 1. What is Collection?
###### 2. What are the main interfaces in collection?
###### 3. What is HashMap? How it stores and retrive the data?
###### 4. What is WeakHashMap?
###### 5. What is ArrayList?
###### 6. What is LinkedList?
###### 7. What is Queue?
###### 8. What is Set?
###### 9. What is Vector?
###### 10. What is Stack?
###### 11. What is TreeSet?
###### 12. What is HashSet?
###### 13. What is difference between ArrayList and LinkedList?
###### 14. What is difference between ArrayList and Vector?
###### 15. What is difference between Set and LinkedList?
###### 16. What is LinkedHashMap?
###### 17. What is Iterator?
###### 18. What is Stream API?

## Design Pattern
###### 1. What is design pattern and it's type?
###### 2. What is observer observable pattern?
###### 3. What is singleton pattern?
###### 4. What is thread interning?
###### 5. How to create singleton class?
###### 6. How to create immutable class?
###### 7. What will happen if I create a clone of singleton object?
###### 8. What are the difference between MVP and MVVM?



