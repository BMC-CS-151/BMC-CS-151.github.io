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


#### Classes
{% highlight tcsh %}
$ ls -lah file.txt #print the size of file.txt in bytes (also the date it was created)
$ wc -l file.txt #print the number of lines in file.txt
$ file file.txt #print the type of the file (e.g. is it a text file? compressed archive?)
$ head file.txt #print the first 10 lines of file.txt
$ head -NUM file.txt #print the first NUM lines of file.txt (e.g. head -3 prints first 3 lines)
$ tail -NUM file.txt #print the last NUM lines of file.txt (e.g. tail -3 prints last 3 lines)
$ cat file.txt #print the entire contents of file.txt
$ tar -xzvf file.tar.gz #unzip a tar archived file
$ tar -czvf files.tar.gz files/ #create a tar archived file containing the contents of the directory files/
{% endhighlight %}

#### Runtime Complexity
{% highlight tcsh %}
$ sort file.txt # sort the lines in file.txt (by default, alphabetically and ascending)
$ sort -r file.txt # sort the lines in file.txt in reverse order
$ sort -nr file.txt # sort the lines in file.txt numerically and in reverse order
$ uniq file.txt # remove duplicate lines (only works if you use "sort" first)
$ uniq -c file.txt # print out unique lines and the number of times each one occurs
$ cut -f 1 file.txt # print the first column of the file.txt (assumes columns are tab-separated)
$ cut -f 1 -d ',' file.csv # print the first column of file.csv, split on comma instead of tab
$ grep "phrase" file.txt # print out lines in file.txt that contain the string "phrase"
$ grep -i "phrase" file.txt # same as above, but ignoring case
$ grep -v "phrase" file.txt # print out lines in file.txt that don't contain the string "phrase"
$ shuf file.txt # shuffle the lines in file.txt
{% endhighlight %}

#### Gettin' fancy
Bash commands are connecting via "pipes", which means the input of one command is the output of the previous command. We use the | character to "pipe" one command's output into another. Below are some useful examples.
{% highlight tcsh %}
$ cat file.txt | sort | uniq | wc -l # how many unique lines are in this file
$ cat file.txt | sort | uniq -c | sort -nr # print out the unique lines in file.txt, with the most frequent line and its count at the top
$ cat file.txt | grep "phrase" | wc -l # how many lines in this file contain the phrase "phrase" 
$ cat file.txt | sort | uniq -c | sort -nr | head -100 | shuf | head -10 # take a random sample of 10 of the top 100 most frequent lines
{% endhighlight %}
Bash can also write to files! This makes a life a lot easier than dragging your cursor, copying large chunks of text from the terminal window. File Output Redirection can be done using the <code> > </code> or <code> >> </code> operators. 
{% highlight tcsh %}
$ grep "Hello" file.txt > output.txt # Stores every line containing "Hello" in file.txt in a new file output.txt
$ cat file.txt | sort | uniq -c | sort -nr > output.txt # stores the unique lines of file.txt, with the most frequent line and its count at the top, in output.txt. Overwrites the old contents of output.txt (Careful!)
$ cat output.txt | wc -l >> output.txt # Appends the line count of output.txt to the end of output.txt
{% endhighlight %}

#### Downloading Files
To download the contents of any URL (whether it be a file, HTML page or even a picture), there's a very useful command on Mac and Linux.
{% highlight tcsh %}
$ wget https://cs.brynmawr.edu/cs113/website/hws/HW00.html # Downloads the contents of the URL as the file 'HW00.html' to the current directory (used in Linux)
{% endhighlight %}
{% highlight tcsh %}
$ curl -O https://cs.brynmawr.edu/cs113/website/hws/HW00.html # Downloads the contents of the URL as the file 'HW00.html' to the current directory (used in Mac)
{% endhighlight %}

#### Uploading Files and Directories
To turn in your HWs, you will need to upload files to Gradescope. If you are accessing the CS lab machines remotely, you will need to copy the files over onto your own computer to upload to Gradescope. 
There are some commands below which show how to transfer your HW files from the lab machine to your local computer over SSH. The <code>:~/</code> at the end is required always. For directories, the <code>-r</code> flag is required. 
{% highlight tcsh %}
$ scp  username@serveraddress:/home/username/path-to-file/your_file_name . # This copies the file "your_file_name" from the remote server to your computer. 
$ scp johndoe@goldengate.cs.brynmawr.edu:/home/johndoe/CS113/hw10/README.txt . # This copies README.txt to your current directory. 
$ scp -r username@serveraddress:~/home/username/path-to-dir . # This copies the entire directory "your_dir" from the remote server to your current directory on your own computer.
$ scp -r johndoe@goldengate.cs.brynmawr.edu:~/home/username/CS113/hw09 # This copies the hw09 directory from the remote server to your computer.
{% endhighlight %}

#### VIM
We will be using vim/vi as our text editor. vim is a powerful editor. Make sure to do the vim tutorial linked to in the first lab. 
Here are some of the most common things you need to remember about vim

This [cheat sheet](https://vim.rtorr.com/) lists lots of useful vim commands on one page.

{% highlight tcsh %}
`i` starts an interactive session
`ESC` will end interactive mode
`:` is how you specific many command
`:w` writes/saves the file
`:q` quits vim
`:q!` quits vim without saving changes
`:! <...>` will run a bash command. For example `:! ls` will list the files in the directory you are currently in
{% endhighlight %}

