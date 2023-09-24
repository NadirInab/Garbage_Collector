<div align="center"> 
<h1>  Garbage_Collector<h1>
<p >This repository provides in-depth information and resources about the Java Garbage Collector .</p>
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
  
- **Platform Independence**
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
- ``Reachability and Object Eligibility``
- ``Young Generation``
- ``Old Generation (Tenured Generation):``
- ``Permanent Generation``

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

### Simple ex 👍 : 

```java
  public class MemoryManagementExample {
    public static void main(String[] args) {
        String message = new String("Hello, Earth From JAVA");
        
        message = null;
    }
}
```
#### In Java, memory is divided into two main areas: 

<div align="center">
  <img src="https://miro.medium.com/v2/resize:fit:1000/1*k8DpgOO1fpigrZIeBtDhWA.png" alt="Image Alt Text">
</div>

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

```md****

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

        // Local variable stored on the stack
        String message = "Hello, World!";
    }

    public static int calculateSum(int a, int b) {
        // Local variable stored on the stack
        int sum = a + b;
        return sum;
    }
}

```
</div>

<div>
  
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

```java
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

## Disclaimers
