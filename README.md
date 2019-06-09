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

Instance initialization block / Init block are used to initialize data members, its is executed whenever class is initialized and before constructors are invoked.

```
class Example 
{
    // Instance initialization block
    {  
        System.out.println("IIB block"); 
    }
    
      public Example()
      {
           
      }
}
```

**10. What is Generics in Java?**

Generics enables types like Integer, String, User Defined types to be parameters when defining classes, interfaces and methods.

BENEFITS:

-  Type parameters provide a way to reuse the same code with different inputs.

- Strong type check at compile time.

- Elimination of type cast.

```
List list = new ArrayList(); // Non-Generic
list.add("Ashish");
String name = (String)list.get(0); // Casting is required

// Generic
List<String> list = new ArrayList<>();
list.add("Ashish");
String name = list.get(0); // No Casting is required
```

**11. What is difference between Annoymous Inner Class and Lambda Exp.?**

- Lambda Expression work with Single Abstract Method (SAM) types that is Interface with single abstract method. It will fail as soon as your interface contains more than one abstract method.
That is where Anonymous class is used.

- At runtime annonymous class require class loading, memory allocation, and object initialization and invoking of non static method, whereas lambda expression is pure compile time activity.


**12. What are the checked and unchecked exceptions?**

###### Checked Exception:
The classes which directly inherit Throwable class except RuntimeException and Error are known as checked exceptions e.g. IOException, SQLException etc. Checked exceptions are checked at compile-time.

###### Unchecked Exception: 
The classes which inherit RuntimeException are known as unchecked exceptions e.g. ArithmeticException, NullPointerException, ArrayIndexOutOfBoundsException etc. Unchecked exceptions are not checked at compile-time, but they are checked at runtime.

###### Error:
Error is irrecoverable e.g. OutOfMemoryError, VirtualMachineError, AssertionError etc.

**13. What is the difference between exception and error?**

###### Exception:
An Exception "indicates conditions that a reasonable application might want to catch."

###### Error:
An Error "indicates serious problems that a reasonable application should not try to catch."

Errors are also unchecked exception & the programmer is not required to do anything with these. In fact it is a bad idea to use a try-catch clause for Errors. Most often, recovery from an Error is not possible & the program should be allowed to terminate. Examples include `OutOfMemoryError`, `StackOverflowError`, etc.

**14. What is dependecy injection?**

Dependency injection is a concept, and according to this a class should not configure its dependencies statically but it should configured from outside.
A class has a dependency if it uses an instance of another class.

Let’s say we have a car class which contains various objects such as wheels, engine, etc. Inside the Car class we are creating the Wheel and Battery. Now if someday we want to change the brand/company of the wheen and battery, we have to create a new Car object with desired wheel and battery brand. BUT if we use DI, we can change the wheel and battery brand at runtime, by providing these two dependecy from outside.

**15. What is HashCode?**

Hash code is an unique integer value for unique object that is returned by `hashCode()` method of Object class.
This method is also used to search a value in collection.
JVM uses hashCode method while saving object into hashing related data structure.

## String
**1. What is String interning?**

String Interning is a method of storing only one copy of each distinct String Value, which must be immutable.

**2. What is String pool?**

String pool is special memory area where Strings are stored by JVM. The JVM can optimize the anount of memory allocated for the Strings by storing only one copy of each string literal in the pool. When we create a string variable and assign value to it JVM searches pool for value of the string. If found, Java compiler returns a reference to it's memory address.

## Multithreading
**1. What is thread interning?**

String Interning is a method of storing only one copy of each distinct String Value, which must be immutable.

**2. What is the lifecycle of a thread?**

A thread is an independent path of execution in the program. Multiple threads can run concurrently with in a program.
A thread lies only in one of the shown states at any instant:

1- New
2- Runnable
3- Blocked/Waiting
4- Timed Waiting
5- Terminated

###### 1. New State:
When a new thread is created, it is in the new state. The thread has not yet started to run when thread is in this state. When a thread lies in the new state, it’s code is yet to be run and hasn’t started to execute.

###### 2. Runnable State:
A thread that is ready to run is moved to runnable state. In this state, a thread might actually be running or it might be ready run at any instant of time. It is the responsibility of the thread scheduler to give the thread, time to run.

###### 3. Blocked/Waiting State:
When a thread is temporarily inactive, then it’s in one of the following states:
Blocked
Waiting
For example, when a thread is waiting for I/O to complete, it lies in the blocked state. It’s the responsibility of the thread scheduler to reactivate and schedule a blocked/waiting thread. A thread in this state cannot continue its execution any further until it is moved to runnable state. Any thread in these states does not consume any CPU cycle.

###### 4. Timed Waiting State:
A thread lies in timed waiting state when it calls a method with a time out parameter. A thread lies in this state until the timeout is completed or until a notification is received. For example, when a thread calls sleep or a conditional wait, it is moved to a timed waiting state.

###### 5. Terminated State:
A thread terminates because of either of the following reasons:
- Because it exists normally. This happens when the code of thread has entirely executed by the program.
- Because there occurred some unusual erroneous event, like segmentation fault or an unhandled exception.


**3. What is yield() method?**

`yield()` method is use to prevent the execution of a thread in between if something important is pending. yield basically means that the thread is not doing anything particularly important and if any other thread need to be run, they should run. Otherwise the current thread will be continued. Its gives hint to the thread schedular that its ready to pause its execution. Thread schedular is free to ignore this hint. IF ANY THREAD EXECUTES YIELD METHOD, THREAD SCHEDULAR CHECKS IF THERE IS ANY THREAD WITH HIGHER OR SAME PRIORITY THAN THIS THREAD. IF SCHEDULAR FINDS ANY THREAD CURRENT THREAD WILL BE MOVED TO READY/RUNNABLE STATE AND GIVE PROCESSOR TO OTHER THREAD, IF NOT CURRENT THREAD WILL KEEP EXECUTING.

`Thread.yield();`

**4. What is difference between process and thread?**

Process is basically a program in execution whereas Thread is a lightweight process or subprocess. 

**5. What is join() method?**

`join()` method puts the current thread on wait until the thread on which it is called is dead. 
Its can be used to create a execution sequence for multiple thread to execute.

**6. What is difference between wait() and sleep() method?**

There is a difference between `wait()` and `sleep()`. `wait()` will wait until the timeout expires or the thread finishes. 
`sleep()` will just wait for the specified amount of time unless interrupted. So it is perfectly possible for `join()` to return much faster than the specified time.

**7. What is difference between wait() and join() method?**

`wait()` is declared in Object class whereas `join()` is declared in Thread.

**8. What is thread scheduler?**

A thread scheduler is the part of the operating system in charge of deciding which threads in the system should run, when, and for how long. Android’s thread scheduler uses two main factors to determine how threads are scheduled across the entire system: nice values and cgroups.

**9. What is thread scheduler?**

**10. What is Looper?**

Looper is a class which is used to execute messages(runnable) in a queue. It is responsible to create a queue in a thread.

###### 11. Why the notify() and notifyAll() methods are part of Object class instead of Thread classh?

**12. What is thread pool?**

A thread pool is a collection of threads, it reuses previously created threads to execute current task and offers a solution to the problem of resource thrashing and time consuming

**13. What is difference betweeen == operator and equals() method?**

We use == for reference (address) comparision and equals() method for content comparision.
== is an operater and equals() is a method.

###### 14. What is Autoboxing and Unboxing?
**15. What is the differenve between Comparable and Comparator?**

Comparable

1- Comparable interface is a default interface for sorting the objects in Java. All the classes like String, Integer have implemented the comparable interface.
2- Comparable interface provides compareTo(Object o) method for specifying the sorting logic.

Comparator

1- Comparator interface is used when the class have not implemented comparable interface, or you have to provide your own/different sorting logic.
2- Comparator interface provides compare(Object ob1, Object ob2) for specifying the sorting logic.

**16. What are the synchronous and asynchronous?**

When we execute something synchronously, we wait for it to finish before moving on to another task.
When we execute somethng asynchroously we can move on another task before it finishes.

## Object Oriented Programming
###### 1. What is thread interning?
###### 2. What is encapsulation?

**3. What is polumorphism?**

Polymorphism is a concept in which we can perform a single action in different ways.

**4. What is compile time and runtime polymorphism?**

**Dynamic Method Dispatch/Dynamic Binding/ Runtime Polymorphism** is a process in whitch call to an overridden method is resolved at runtime rather than compile time. In this process an overridden method is called through reference variable of super class. Determination of the method to be called is based on the object is being referred to by reference variable.

###### 5. Why return type does not play role in method overloading?
**6. What is upcasting in Java?**

If the reference variable of Parent class referes to the object of child class, its is known as Upcasting.
Example: We have a class A and class B. Class B extends class A. so we can write below:

`A a = new B()`

###### 7. What is default method in Java?
###### 8. What is difference between interface and abstract class(after Java 8)?
###### 9. What is difference between default method and static method?
###### 10. What is Enum in Java?
###### 11. What is Generics?
###### 12. What are the interfaces that are implemented in String class?
###### 13. Can we create objetc of interface and abstract class?
**14. What is Constructor chaning?**

Constructor Chaining is the process of calling one constructor from another constructor with respect to current object.
Constructor Chianing can be done in two ways.

1- Within class using this()
2- From base class  using super() (inheritance is needed)

Super and this statements should always be the first line of the cunstrctor.

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



