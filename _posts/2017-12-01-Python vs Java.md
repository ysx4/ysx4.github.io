---
layout: post
title: "Python vs Java"
author: "学习的Yang"
categories: techynotes
tags: [concept,language]
techy: true
---
### Python and Java
*The Language is a language specification - you don't write a language in a language, it's a specification. That would be like asking "Do you write French in German?" What I'm assuming the questioner really wanted to know is - what is the underlying language the entire Java Virtual Machine (or Python interpreter) and Class libraries developed in.*

* **Python** - The Python programming language can be written in any language. Python has a compiler! You just don't notice it because it runs automatically, it does not compile to the native machine's code, instead, it compiles to a byte code that is used by a virtual machine. The most used interpreter is CPython which is written in C. But there are many alternatives like for example Jython which is written in Java, pypy which is written in python itself or ironpython which is written in C#.
* **Java** - The Sun JVM is written in C, although this need not be the case - the JVM as it runs on your machine is a platform-dependent executable and hence could have been originally written in any language. The Java libraries (java.lang, java.util etc, often referred to as the Java API) are themselves written in Java, although methods marked as native will have been written in C or C++.

> Python和Java都是需要编译然后运行的在虚拟机上的语言。Python一般是全自动的，所以装一个编译器就可以直接运行程序，而Java则需要先编译，然后在任何装有JVM的环境下运行。

### Similarity and Difference
The biggest similarity is their "(almost) everything is an object" design and their reputation for excellent cross-platform support, as well as things like immutable strings and deep, relatively standard libraries.

There are big differences, too. At the community level, Java has always had a single large corporate sponsor. Python support is more distributed. Although both are well within the Algol-like family of languages, Python's use of syntactically-significant whitespace sets it a little further apart from the mainstream than Java, which is comfortably familiar in its C-like use of braces and semi-colons.

Both languages are compiled down to bytecodes that run on virtual machines, although Python generally does this automatically at runtime and Java has a separate program (javac) that does it. The virtual machines largely isolate the languages from the vagaries of the underlying hardware. Many Java virtual machines (JVMs) have the ability to do just-in-time compilation of parts of the bytecode down to the native instruction set of whatever platform it happens to be running on, which can produce significant speed-ups.

> 最大的相同点就是，都是面向对象的语言。最大的不同，语法上Python利用程序本身的空格与对齐来区分程序块，Java则有花括号和分号；还有就是赞助商的不同，Java是一个大金主，Python是众多小金主。

### Big difference - Duck Typing
The biggest difference between the two languages is that Java is a statically typed and Python is a dynamically typed.

Python is strongly but dynamically typed. This means names in code are bound to strongly typed objects at runtime. The only condition on the type of object a name refers to is that it supports the operations required for the particular object instances in the program. For example, I might have two types Person and Car that both support operation "run", but Car also supports "refuel". So long as my program only calls "run" on objects, it doesn't matter if they are Person or Car. This is called "duck typing" after the expression "if it walks like a duck and talks like a duck, it's a duck".

This makes Python very easy to write and not too bad to read, but difficult to analyze. Static type inference in Python is a known hard problem. The lack of type information in function signatures combined with support for operator overloading and just-in-time loading of modules at runtime means that the most common type inference algorithms have nothing to work with until the point in the program's execution when the types are known anyway. 

The downside is that not having type information means it can be hard to tell what is going on at any given place in the code, particularly when names are ambiguous, which they frequently are.

Java, in contrast, is statically typed. Names in Java are bound to types at compile time via explicit type declaration. This means many type errors that would result in a runtime error--and often a program crash--in Python get caught at compile time in Java. And you can tell at a glance what type of object a name is associated with in Java, which makes analysis by humans as well as compilers much easier.

This means that Java depends critically on well-designed types, while Python requires very little type design. This is what makes Python a great prototyping language, and is also what makes it a good teaching language and a good language for people who aren't software professionals. 

> Python是动态型，就是直到你要用的时候才会关心一个变量是什么。Java是静态型，在写程序的时候就要求清楚知道自己在写什么。

##### *For Java Dev*
> * The Java design has an interesting mix of atomic types built into the language. In Python this isn't possible, but there is a superset of Python called Cython that allows users to specify types where having that information could result in faster code being emitted by the compiler. Careful use of this extended version of the language can result in considerable performance improvement.
> * There is a version of Python called Jython that compiles to JVM byte-codes, allowing very simple integration of Python with Java, and which gives Python programmers access to Java's deep and powerful libraries.

## Comparision

### Speed (Java better)
* Neither Java nor Python is especially suited to high-performance computing
* Although some Python implementations, such as PyPy, are fine-tuned for performance, raw portable performance is not where Python shines.
* A lot of Java efficiency comes from optimizations to virtual machine execution. A JVM can translate bytecode into native machine code as a program executes. This Just-In-Time (JIT) compilation is why Java’s performance can often rival that of native languages. 

### Syntax
* Python is unusual among programming languages in that it uses indentation to separate code into blocks. 
* Java, like most other languages, uses curly braces to define the beginning and end of each function and class definition. 
* The advantage of using indentation is that it forces you to set your program out in a way that is easy to read, and there is no chance of errors resulting from a missing brace.

### Legacy (Python has less)
* Java’s history in the enterprise and its slightly more verbose coding style mean that Java legacy systems are typically larger and more numerous than Python legacy.
* organizations may be surprised to find how many of the scripts and glue code that hold their IT infrastructure together are made up of Python.

### Practical Agility (Both work well)
* Python has always had a presence in the agile space and has grown in popularity for many reasons, including the rise of the DevOps movement.
* Java enjoys more consistent refactoring support than Python thanks on one hand to its static type system which makes automated refactored more predictable and reliable, and on the other to the prevalence of IDEs in Java development (IntelliJ, Eclipse, and NetBeans, for example).

### Human Resources (Completely depend on the company)
* Sometimes language choice is more about the application of skills than it is about the software applications themselves. Staffing may count for more than language design and tooling.
* Java has consistently been more popular than Python, but Python has experienced the greater growth of the two languages, picking up where Perl and Ruby are falling.

### Architecture
* Software architecture is a matter of skills, existing software systems, frameworks and libraries, reuse, and integration. 
* Both Java and Python enjoy a seemingly endless supply of open-source libraries populated by code from individuals and companies who have solved common and uncommon problems, and who are happy to share so others can take advantage of their solutions. 

