---
layout: default
title: "CheckStyle, Stacks, Unit Testing"
type: Lab
number: 05
active_tab: lab
release_date: 2023-10-04

---

<!-- Check whether the assignment is ready to release -->
{% capture today %}{{'now' | date: '%s'}}{% endcapture %}
{% capture release_date %}{{page.release_date | date: '%s'}}{% endcapture %}
{% if release_date > today %} 
<div class="alert alert-danger">
Warning: this assignment is out of date.  It may still need to be updated for this year's class.  Check with your instructor before you start working on this assignment.
</div>
{% endif %}
<!-- End of check whether the assignment is up to date -->


<!-- Check whether the assignment is up to date -->
<!--{% capture this_year %}{{'now' | date: '%Y'}}{% endcapture %}
{% capture due_year %}{{page.due_date | date: '%Y'}}{% endcapture %}
{% if this_year != due_year %} 
<div class="alert alert-danger">
Warning: this assignment is out of date.  It may still need to be updated for this year's class.  Check with your instructor before you start working on this assignment.
</div>
{% endif %}-->
<!-- End of check whether the assignment is up to date -->



{% if page.materials %}
<div class="alert alert-info">
You can download the materials for this assignment here:
<ul>
{% for item in page.materials %}
<li><a href="{{item.url}}">{{ item.name }}</a></li>
{% endfor %}
</ul>

</div>
{% endif %}





{{page.type}} {{page.number}}: {{page.title}}
=============================================================


## Objectives:

The main goals for this lab are:
1. Get practice using a checkstyle
1. Work with Stacks
1. Get started with JUnit

You will need to have a TA check off on all your exercises.
If you do not complete the lab during the lab session, you
must have a TA check off all your exercises during office hours.
You must get this lab checked off by the due date for HW04.

### Paired Programming rules
This lab is a **paired programming assignment.** What exactly does that mean? 
You will be working in pairs on the CS lab computers. Each pair will be working on one computer. One person will be the **driver** and the other person
 will be the **navigator**. Here is the rule: the **driver** controlls the lab computer, but the **driver** can only type what the **navigator** tells 
them to type. For this to work well, each pair should be constantly talking 
among themselves. After each problem, you will switch roles, the navigator will become the driver and the driver will become the navigator.

## Exercise 1 - Checkstyle

<s>On Tuesdays</s> During Monday's (good catch Jude!) class we introduced checkstyle. Checkstyle is an open-sourced tool that 
allows one to easily check whether their code complies with customizable rules.

Your task is to modify `HelloWorld.java` from `lecture08` so that the checkstyle passes.

Getting Started:
1. Download the xml checkstyle from the course GitHub repository. You can find it under `res/`.
1. Download the checkstyle-8.16 jar file (look at slide 9 from lecture 08 on where to download it from.
1. Run 
	```java -jar checkstyle-8.16-all.jar –c  cs151_checks.xml HelloWorld.java```
to see the checkstyle errors.
1. Modify `HelloWorld.java` until the above command runs without any errors.

## Exercise 2 - PostfixEvaluator.java

Download `PostfixEvaluator.java` from 
<a href="{{ site.url }}{{ site.baseurl }}/labs/lab05/PostfixEvaluator.java">{{ site.url }}{{ site.baseurl }}/labs/lab05/PostfixEvaluator.java</a>
This is an implementation of the postfix evaluator we discussed in class with the built-in Java `Stack`.
Look through the code to understand how it work. Run `PostfixEvaluator.java` to interact with it a bit.

### Exercise 2.1 - Testing PostfixEvaluator
Run the tests we provide in `TestPostFixEvaluator`.

You can download `TestPostfixEvaluator.java` from 
<a href="{{ site.url }}{{ site.baseurl }}/labs/lab05/TestPostfixEvaluator.java">{{ site.url }}{{ site.baseurl }}/labs/lab05/TestPostfixEvaluator.java</a>

**Make sure the checkstyle passes for `TestPostfixEvaluator.java`**.
When you run the checkstyle for `TestPostfixEvaluator` you will see `7` errors. Fix all them
and then continue.

Once the test file passes the checkstyle, you will run the tests. To run the tests,
you will need to make sure you download two jar files:
1. junit-4.13.2.jar - https://repo1.maven.org/maven2/junit/junit/4.13.2/
1. hamcrest-core-1.13jar - https://repo1.maven.org/maven2/org/hamcrest/hamcrest-core/1.3/

To compile and run the tests, run the following command:

```bash
javac -cp junit-4.13.2.jar  *.java
java -cp "./junit-4.13.2.jar:./hamcrest-core-1.3.jar:./" org.junit.runner.JUnitCore TestPostfixEvaluator
```

Test it using TestPostfixEvaluator.java. Make sure you understand how it works.

Now, add 4 more tests to `TestPostfixEvaluator`. The tests should each combine multiple operators.

### Exercise 2.2 - Modifying PostfixEvaluator

Copy `PostFixEvaluator.java` to a new file called `PostfixStringEvaluator.java`.
Modify `PostfixStringEvaluator.java` to convert a postfix expression to a parenthesized infix 
expression and display it to the user. Modifications to `PostfixStringEvaluator.java` should not be
extensive. The only difference is that when encountering an operator, instead of pushing the
result of the arithmetic operation involving this operator and the top two operands onto the
stack, i.e. a number, you will consruct the string representing that arithmetic operation and
push the string onto the stack instead. Below are some examples:

```
Sample Input 1
5 6 + 9 *
Output
( ( 5 + 6 ) * 9 )
Sample Input 2
8 9 10 + *
Output
( 8 * ( 9 + 10 ) )
```

Make sure `PostFixEvaluator.java` complies with the style guide.

### Exercise 2.2 - Testing PostfixStringEvaluator
We provide three tests in `TestPostfixStringEvaluator`. 

You can download `TestPostfixStringEvaluator.java` from 
<a href="{{ site.url }}{{ site.baseurl }}/labs/lab05/TestPostfixStringEvaluator.java">{{ site.url }}{{ site.baseurl }}/labs/lab05/TestPostfixEvaluator.java</a>

Again, make sure that `TestPostfixStringEvaluator.java` passes the checkstyle.
There will be `7` checkstyle errors in the file we are providing you.

Now add 4 more tests, make them a bit complicated.

## Excercise 3 - DoubleStack

Now we are going to imlement 2 stacks using 1 array.

Imlement a `DoubleStack` class using a single underlying array 
that stores two different stacks (stack 1 and stack 2).
One of the stacks grows upwards
from index 0 upward, and the other stacks grows from the end of the array down. So these two stacks
grow towards each other. 

The top indexes are denoted by `top1` and `top2` for stack 1 and
stack 2, respectively. Thus, the `DoubleStack` class should have three instance variables: 

1. E[] theArray, 
1. int top1,
1. int top2

Make sure `theArray` locations 0 to top1 contain elements in stack 1 and theArray locations
theArray.length-1 downto top2 stores the elements in stack 2.

### Methods to implement

Implement the following methods.

If the runtime of any of the methods besides for `printStack` is not
`O(1)`, you are writing unnecessary loops.

Before implementing the tests, make sure to create a test fille called `TestDoubleStack.java`
that uses JUnit tests.

#### 3.1 push(int stackId, E e): 
push e onto stack stackId (1 or 2). In other words, it
will push onto stack 1 if stackId==1 and onto stack 2 if stackId==2. Throw an
`IllegalStateException` if stack is full.

#### 3.2 E pop(int stackId): 
pop from stackId, return null if empty.

#### 3.3 E top(int stackId): 
top element from stackId, return null if empty.


#### 3.4  int size(int stackId): 
return size of stack stackId

#### 3.5  boolean isEmpty(int stackId)

#### 3.6  printStack(int stackId)

## Wrap up

In todays lab we covered checkstyle, stacks, and unit testing.

### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
If you do not finish the lab in time, you will need to go to office hours so
that a TA can check your work.


