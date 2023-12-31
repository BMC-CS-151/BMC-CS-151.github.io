---
layout: default
title: "AVL Trees"
type: Lab
number: 10
active_tab: lab
release_date: 2023-12-06

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
1. Getting practice with AVL Trees and Rotations


### Paired Programming rules
This lab is a **paired programming assignment.** What exactly does that mean? 
You will be working in pairs on the CS lab computers. Each pair will be working on one computer. One person will be the **driver** and the other person
 will be the **navigator**. Here is the rule: the **driver** controlls the lab computer, but the **driver** can only type what the **navigator** tells 
them to type. For this to work well, each pair should be constantly talking 
among themselves. After each problem, you will switch roles, the navigator will become the driver and the driver will become the navigator.


## Exercise
In this assignment you will write a AVLTee that extends your LinkedBinaryTree
from HW05.

### 1 
Add a `parent` reference and a `height` instance variable to the `Node` class of 
`LinkedBinaryTree`.
Inheritance of inner/nested classes of Java could be weird so it’s easier to just make changes
to the `Node` in `LinkedBinaryTree` instead.

### 2
Modify/override `LinkedBinaryTree` and/or `AVLTree` so that `parent` and `height`
are set correctly on `insertion` and `deletion`. 
You might need additional helper methods (to compute
`height`, for example).

### 3
Override `toString` of the `Node` class to print the element followed by its 
`height` in parenthesis.

### 4
Modify/Override `toStringInOrder` so that it uses the above `toString` of `Node`
and returns a traversal string listing the elements with `height` attached.

### 5
Implement `rebalance` with associated helpers (rotateLeft, rotateRight, rotateLeftRight,
rotateRightLeft) and call appropriately on insertion.

### 6 - Testing
Create an `AVLTree<String>` and insert the exercise example given in class, i.e. “M”, “N”,
“O”, “L”, “K”, “Q”, “P”, “H”, “I”, “A” and the final balanced tree should look like this:

![](lab10.png)

### 7 
Override `toString` of `AVLTree` to print out the in-order traversal, with the height of each
node attached. For example, the tree above should return the following string:

```
A(1) H(2) I(3) K(1) L(2) M(1) N(4) O(1) P(2) Q(1)
```
# Summary

In this lab we covered AVL Trees.

### Signing out
Before leaving, make sure your TA/instructor have signed you out of the lab. If you finish the lab early, you are free to go.
If you do not finish the lab in time, you will need to go to office hours so
that a TA can check your work. This lab must be completed by Thursday December 14th.
