<div align="center">
     <img src="https://www.itprotoday.com/sites/itprotoday.com/files/java-logo_0.jpg" alt="Image Alt Text">
</div>

![Java](https://img.shields.io/badge/JAVA-green.svg)
![Java](https://img.shields.io/badge/JDK-aqua.svg)
![Java](https://img.shields.io/badge/JRE-brown.svg)
![Java](https://img.shields.io/badge/JVM-khaki.svg)
![Java](https://img.shields.io/badge/JAVAC-purple.svg)
![JavaDoc](https://img.shields.io/badge/javaDocs-yellow.svg)
![JavaDoc](https://img.shields.io/badge/Garbage_Collector-red.svg)
![JavaDoc](https://img.shields.io/badge/Memory_management-gray.svg)
![JavaDoc](https://img.shields.io/badge/Young_Generation-gold.svg)
![JavaDoc](https://img.shields.io/badge/Old_Generation-indigo.svg)
![JavaDoc](https://img.shields.io/badge/Heap-orange.svg)
![JavaDoc](https://img.shields.io/badge/Stack-orchid.svg)

<div align="center"> 
<h1>  Garbage_Collector<h1>


  
<p>This repository provides in-depth information and resources about the Java Garbage Collector .</p>
</div>

<div> <h3> To get a better understanding of deeper concepts, let's do a brief recap, about the following :  </h3> </div>

<div> 
  
- **What is JAVA**
- **What is JDK**
- **What is JRE**
- **What is JVM**

</div>
<div>
  <h2 align="center"> What is JAVA</h2>
  <b>In simple words, Java is a popular programming language that allows developers to create applications that can run on various devices and operating systems.</b>
</div>

</div>
<div >
  <h2 align="center">Java Development Kit (JDK)</h2>
  <b>The JDK is a software package that includes the JRE, Java development tools (compiler, debugger, etc.), and additional tools and libraries needed for Java development.</b>
<h2>Features : </h2>
  
- **Java Compiler (javac) and Interpreter (java)**
- **Java Virtual Machine (JVM)**
- **Java API**
- **Java Debugger (jdb)**
- **Java Archive Tool (jar)**
- **Java Documentation Generator (javadoc)**
- **JavaFX**
- **Version Management**
- **As well as many other features we will learn throughout the year**
  
</div>

</div>
<div >
  <h2 align="center">Java Virtual Machine (JVM)</h2>
  <b>The JVM is a crucial component of the Java platform. It's an abstract machine that provides a runtime environment in which Java bytecode can be executed. The JVM translates compiled Java bytecode into native machine code that's specific to the underlying hardware.</b>
<h2>Features : </h2>
  
- **Platform Independence**
- **Just-in-Time Compilation (JIT)**
- **Garbage Collection**
  
</div>

<div >
  <h2 align="center">Java Virtual Machine (JVM)</h2>
  <b>The JVM is a crucial component of the Java platform. It's an abstract machine that provides a runtime environment in which Java bytecode can be executed. The JVM translates compiled Java bytecode into native machine code that's specific to the underlying hardware.</b>
<h2>Features : </h2>
  
- **Platform Independence (WORA)**
- **Just-in-Time Compilation (JIT)**
- **Garbage Collection**
  
</div>

<div >
  <h2 align="center">Java Runtime Environment (JRE)</h2>
  
  <b> The JRE includes everything needed to run a Java application or applet. It consists of the JVM, class libraries (APIs), and other supporting files.
    When you want to run a Java application, you need to have the JRE installed on your system. </b>
    
</div>

<div>
  <h2> In simple terms How JAVA code works </h2>
  
- **Writing Java Code: Developers write Java code using a text editor or an Integrated Development Environment (IDE).**
- **Compilation: The Java source code (.java files) is compiled using a Java compiler (javac), which produces bytecode (.class files).**
- **Execution: The Java bytecode is executed by the JVM (via the java command) on the target system.**
</div>
<h3 align="center" > <h3>
<div align="center">
  <img src="https://static.javatpoint.com/images/jdk2.png" alt="Image Alt Text">
</div>

<div align="center">
     
<h1>What is a Garbage_Collector ?<h1>
<img src="https://miro.medium.com/v2/resize:fit:803/1*kylOt2przGxahWebTuENbg.png" alt="Image Alt Text">
</div>


<div>
  
<h2 align="center" >We will learn about : </h2>
  
-  ``What is Garbage collection in JAVA ?``
-  ``Why do we need garbage collection ?``
- ``What is Memory Management in JAVA ?``
- ``HEAP``
- ``STACK``
- ``Serial Garbage Collector``
- ``Parallel Garbage Collector``
- ``Reachability and Object Eligibility``

</div>

<div>
  
### What is Garbage Collection ? 
  
  ```md

      In simple terms Garbage collection is the process of automatically 
      reclaiming memory occupied by objects that are no longer
      reachable or in use by the application.

   ```

```md

  Because forgetting to destroy unused objects will lead to memory leaks, After a
  certain point, memory won't be available anymore to create new objects,
  eventually the entire app  will stop due to Out-Of-Memory-Errors.

 ```

</div>

<div>
  
### What is Memory Management ?

  ```md

    Memory management is the process of controlling and organizing a computer system's 
    memory resources, which includes allocating memory to programs and 
    data structures when needed and releasing it when 
    no longer required.

 ```

#### Simple ex in C 👍 : 

```c

#include <stdio.h>
#include <stdlib.h>

int main() {
    // Allocate memory for an integer
    int *num = (int *)malloc(sizeof(int));

    // Check if memory allocation was successful
    if (num == NULL) {
        printf("Memory allocation failed.\n");
        return 1;  // Exit with an error
    }

    // Assign a value to the allocated memory
    *num = 42;

    // Print the value
    printf("Value: %d\n", *num);

    // Deallocate the dynamically allocated memory
    free(num);

    return 0;
}

```

### Simple ex  in java 👍: 

```java

  public class MemoryManagementExample {
    public static void main(String[] args) {
        String message = new String("Hello, Earth From JAVA");
        
        message = null;
    }
}

```

#### Generally speaking the memory is divided into two main areas: 


- ``the heap in general ``

    ```md
  
     The heap is a dynamic and flexible region of memory where data is allocated and 
     deallocated at runtime. Memory in the heap can be accessed in a random
     or arbitrary order.Since memory in the heap is allocated 
     explicitly, there's a risk of memory leaks if
     deallocation is not managed properly.
  
     ```
  
- ``the heap in JAVA ``

    ```md
  
   The heap is where objects and their associated data are stored.

   Heap stores the actual objects. It creates when the JVM starts up. When you use 
   the new keyword, the JVM creates an instance for the object 
   in a heap. While the reference of that object stores
   in the stack. There exists only one heap foreach
   running JVM process. When heap becomes full,
   the garbage is collected.
  
     ```

- ``the stack``

```md

 stack is an abstract data structure that follows the Last-In-First-Out (LIFO) principle.
 stacks are crucial for managing function calls, recursion, expression evaluation,
 and various algorithms where the order of operations or processing
 needs to be controlled.

```

```java

  public class HeapExample {

    public static void main(String[] args) {
        int stackVariable = 42;  // Variable stored on the stack

        // object stored in the heap
        TestClass heapObject = new TestClass();

        // Calling a method that creates a variable stored on the stack
        int result = calculateSum(10, 20);
    }

    public static int calculateSum(int a, int b) {
        // Local variable stored on the stack
        int sum = a + b;
        return sum;
    }
}

```


<div align="center">
  <img src="https://miro.medium.com/v2/resize:fit:1000/1*k8DpgOO1fpigrZIeBtDhWA.png" alt="Image Alt Text">
</div>

</div>

<div>
     
### OverAll Recap 
     
```md
     
          Now let's make it simplier : Given the name, it seems like Garbage Collection would deal with
          finding and deleting the garbage from the memory. However, but in reality,
          Garbage Collection tracks each and every object available in the
          JVM heap space, and removes the unused ones. Basically,
          GC works in two simple steps, known as Mark and Sweep:
         
```

```md
          Mark – this is where the garbage collector identifies which pieces of memory 
          are in use and which aren’t.
          Sweep – this step removes objects identified during the “mark” phase.
```
     
</div>

### GC Implementations

<div>
     
### JVM has five types of GC implementations:

- **Serial GC**
- **Parallel GC**
- **CMS GC**
- **G1 GC**
- **Z GC**

### Now let's check out Serial & Serial GC, but before we do that we need to understand the following : 

- ```Throughput```

```md

Throughput, in the context of GC, refers to the efficiency of the GC in processing and reclaiming memory.
It's a measure of the amount of work done by the garbage collector in a given unit of time.
Higher throughput indicates that the GC is able to process a larger portion
of the heap and reclaim memory quickly, thus maximizing
the application's overall throughput or work done per unit of time.
```

- ```Single Thread```

```md

In the context of garbage collection, a "single thread" refers to the use of only one thread to perform GC operations.
For example, in the Serial Garbage Collector, a single thread is responsible for GC activities.
This approach is simple and suitable for small applications but may have longer
pause times as the single thread performs GC sequentially.
```


- ```Multi-thread```

```md
Multi-thread" refers to the use of multiple threads to perform a task concurrently.
In the context of GC, this means using more than one thread to handle
GC activities simultaneously. 
```
# HERE DOES NOT SHOW

<div align="center">
  <img src="https://i.pinimg.com/originals/a2/22/cc/a222cc08928cd6ce2654214b68c3141b.jpg" alt="Image Alt TeSDSHDSJHDJSDxt">
</div>


### Summary
```md
throughput is a measure of the efficiency of the GC in reclaiming memory, while "single thread" && "multi-thread"
refer to the number of threads involved in performing garbage collection operations, where "multi-thread"
involves using multiple threads to process tasks concurrently, potentially leading to faster
processing and improved efficiency.

```

</div>

<div>
     
### Now Let's dive into : 

- **Serial Garbage Collector** 

```md

Is a simple and basic GC that uses a single thread for garbage collection.
It uses a mark-and-sweep algorithm and is best suited for small
applications or applications that don't require high throughput.

```

#### Marking and sweaping and compacting 

```md

The Serial Garbage Collector first marks the live objects, then sweeps and reclaims memory for the dead
(unreachable) objects, and finally compacts the memory by moving live objects to a compacted area.
 It uses a single thread for these operations, making it simple but less efficient
compared to collectors that use multiple threads.

```

- **Parallel  Garbage Collector** 

```md

AKA the Throughput Collector uses multiple threads for garbage collection.
It's designed to take advantage of multiple CPU cores to improve garbage
collection performance and throughput.  Mmultiple garbage collection
threads work in parallel to scan and collect garbage. His
parallelism can significantly reduce the total time
spenton garbage collection, making it suitable
for applications that prioritize throughput.

```

#### Marking and sweaping and compacting 

```md

the Parallel Garbage Collector utilizes multiple threads to perform these operations in parallel,
which can significantly improve garbage collection performance on multi-core systems.
he parallelism achieved by utilizing multiple threads, making garbage collection
faster on modern computers with multiple processor cores

```

</div>
<div>


#### the heap is allocated into smaller parts, called GENERATIONS.

### Young Generation : 
*     the newly created objects are allocated to the young gen.
### Old Generation : 
*     If the new object requests for a larger heap space, it gets allocated directly into the old gen. Also objects which have survived a few GC cycles gets promoted to the old gen i.e long lived objects house in old gen.
### Permanent Generation 
*      The permanent generation holds objects that the JVM finds convenient to have the garbage collector manage, such as objects describing classes and methods, as well as the classes and methods themselves.

  <div align="center">
  <img src="https://miro.medium.com/v2/resize:fit:1400/1*XXqPGJCxQfri7qE_GrSB8Q.png" alt="Image Alt Text">
</div>

  
### Reachability and Object Eligibility

- ``Reachability``

```md

Reachability refers to the ability of an object to be accessed or reached by the 
program during its execution an object is considered reachable 
if it can be accessed and used by the running program 
through any live reference.

```


- ``Object Eligibility``

```md

An object is eligible for garbage collection when it is no longer reachable,
meaning there are no live references to the object from the program. 
The Java Garbage Collector identifies and reclaims
memory for these unreachable objects.

```

```sh
import java.lang.ref.*;

public class GarbageCollectionExample {

    public static void main(String[] args) {
        // Strong Reference
        MyClass strongRef = new MyClass("Strong Reference");
        
        // Weak Reference
        WeakReference<MyClass> weakRef = new WeakReference<>(new MyClass("Weak Reference"));

        // Soft Reference
        SoftReference<MyClass> softRef = new SoftReference<>(new MyClass("Soft Reference"));

        // Phantom Reference
        ReferenceQueue<MyClass> referenceQueue = new ReferenceQueue<>();
        PhantomReference<MyClass> phantomRef = new PhantomReference<>(new MyClass("Phantom Reference"), referenceQueue);

        // Island of Isolation: Creating a circular reference
        strongRef.setOtherObject(weakRef.get());
        weakRef.get().setOtherObject(softRef.get());
        softRef.get().setOtherObject(phantomRef.get());
        phantomRef.get().setOtherObject(strongRef);

        // Setting references to null to break the island of isolation
        strongRef = null;
        weakRef.clear();
        softRef.clear();
        phantomRef.clear();

        // At this point, the objects in the island of isolation are no longer reachable
        // and are eligible for garbage collection.

        // Perform some operations...

        // ...

        // Force garbage collection (Note: This is just for demonstration, not typically done in real applications)
        System.gc();
    }
}

class MyClass {
    private String name;
    private MyClass otherObject;

    public MyClass(String name) {
        this.name = name;
    }

    public void setOtherObject(MyClass otherObject) {
        this.otherObject = otherObject;
    }

    @Override
    protected void finalize() throws Throwable {
        System.out.println("Finalizing object: " + name);
    }
}


```
</div>

## OverAll 
#### We may create a rabbit hole or a tree of concepts by explaining each concept independently, but I'd love for you guys to discover these concepts as they're very important to our understanding of the GC. 

```md
     Young Generation
     Old Generation
     Permanent Generation
     CMS Garbage Collector
     G1 Garbage Collector
     Z Garbage Collecto
```

## Conclusion 
### garbage collection is a crucial mechanism for automated memory management, ensuring efficient memory usage and reducing the risk of memory-related errors in software applications*

<div align="center">
     <img src="https://present5.com/presentation/245812954_308141166/image-9.jpg" alt="Image Alt Text">
</div>

