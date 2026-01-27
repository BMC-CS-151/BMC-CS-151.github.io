---
layout: default
img: tar
caption: study guide  
title: 151 Prerequisites 
active_tab: 
release_date: 
due_date: 
---

<!-- Check whether the assignment is up to date -->
{% capture this_year %}{{'now' | date: '%Y'}}{% endcapture %}
{% capture due_year %}{{page.due_date | date: '%Y'}}{% endcapture %}
{% if this_year != due_year %} 
{% endif %}
<!-- End of check whether the assignment is up to date -->


CS151 Prerequisites<span class="text-muted">: Study Guide</span> 
=============================================================

The following list of topics are expected knowledge for 151:

- Programming basics
- Control flow
- Strings and command line arguments
- Arrays (Lists)
- Recursion
- Object Oriented Programming and class design
- Runtime Complexity

We recognize that some of these topics may benefit from review, so we have provided a study guide to help you prepare.

#### Java Basics

Java is most different from python in the following ways:

1. **Compilation**: Java is a compiled language. Unlike `.py` files, `.java` files must be compiled before they can be executed. 

    For example given a file `HW1.java`, 

    `javac Hw1.java`

    creates a `.class` file which can be run with:

    `java Hw1`

    The compiler is your friend. It will tell you when there are errors. Compile early and often. 


2. **Hierarchal Structure**: In python you can freely declare variables or write print statements at any level. In java this is not allowed. Everything exists within a class. Statements/Expressions must be inside methods which must be inside classes. 

    In python you can just write,
    ```py
    def f(x):
        return x + 1
    ```

    In java this must exist inside a class:
    ```java
    class Utils {
        int f(int x) {
            return x + 1;
        }
    }
    ```

    Notice that the method `f` has an explicit return type (int) and parameter type (also int). This brings us to our next major difference between python and java...


3. **Static Typing**:  All variables must be declared with *type* of data they are storing.

    Method parameters and return types also must be explicitly declared and are enforced by the compiler.

    Review the following resources:

    [static typing of variables](https://bmc-cs-113.github.io/slides/lecture02.pdf)    
    [Methods in java](https://bmc-cs-113.github.io/slides/lecture04.pdf)


#### User Input

There are two ways to read in data that we will use in this course. The major difference is *when* the data is supplied. 

For **command line arguments** the data is supplied directly when you run the program. For example:
`java Add 5 7`

With the `Scanner`, we can take input while the program is running. For example:
```
$ java Add
Please supply which numbers you would like to add
5
7
```

**Command line arguments** are supplied through the `main` method. This is the entry point of the proggram. It is the first thing that is executed when we run `java ...`

The `main` method has a special syntax: `public static void main(String[] args) { }`

The `args` parameter refers to the command line arguments.

Download and run [this resource](https://github.com/BMC-CS-113/class-examples-s24/blob/main/lecture09/CmdArgs.java) to study reading in command line arguments.


The **Scanner** class:

[Slides](https://bmc-cs-113.github.io/slides/lecture03.pdf) 10-14 discusses the **Scanner** object 

Sample code is shown [here](https://github.com/BMC-CS-113/class-examples-s24/blob/main/lecture04/LeapYears.java).

We recommend you complete the following exercises to study java basics and user input: 

[Exercise 1](https://bmc-cs-113.github.io/hws/HW01.html)   
[Exercise 2](https://bmc-cs-113.github.io/hws/HW02.html)


### Classes
A class groups related variables and methods into a single unit. 

[Slides](https://bmc-cs-113.github.io/slides/lecture14.pdf) 28-43 provide an introduction to classes in java.

The referenced `BankAccount` code is provided [here](https://github.com/BMC-CS-113/class-examples-s24/blob/main/lecture15/BankAccount.java)


Special methods in a class:

- `toString`: 

Java classes have a special method defined as `public String toString()`.

To understand the purpose of a `toString` method, try printing the `account` variable created in the `main` of the `BankAccount` class. 

You should see something like this:
```
BankAccount@2a139a55
```

When printing objects in java, if a `toString()` is not defined, it will print the type of the object (`BankAccount`) and the memory address where it is stored (2a139a55).

Classes are collections of many variables, and it is unclear which variables should be printed if you do not explicitly define it. This is the purpose of a `toString()`. 

Practice adding one for the `BankAccount` class that prints the account name and balance. 

- the `constructor`:

constructors are special methods that are run when an object is created (with the `new` keyword). 
The initialize the object and provide starting values for the variables. 

The constructor has the same name as the class and does not have a return type.


#### Inheritance

The goal of inheritance is to enable reuse of fields and methods in classes. 

Review [slides](https://bmc-cs-113.github.io/slides/lecture16.pdf) 22-38 on inheritance.

The referenced classes are in [this](https://github.com/BMC-CS-113/class-examples-s24/tree/main/lecture17) folder.


We recommend you complete the following exercise to practice your knowledge of classes in Java:
[Exercise 1](https://bmc-cs-113.github.io/hws/HW09.html)
[Exercise 2](https://bmc-cs-113.github.io/hws/HW10.html)


### Runtime Analysis

In 151 we will use mathematical notation used to describe the performance or complexity of an algorithm.
We use this instead of concrete times (seconds or miliseconds) because it is hardware independent. 
Big-O notation represents the upper bound of the time complexity in the worst-case scenario. 
It helps us understand how the runtime of an algorithm grows as the input size increases.

Complete part 1 of [this exercise](https://bmc-cs-113.github.io/labs/Lab11.html) to practice runtime analysis.

