---
num: lab04
ready: true
desc: "Basic Classes in C++"
assigned: 2023-02-23 13:00
due: 2023-03-08 23:59
---

# {{page.num}} - {{page.desc}}


## Goals for this lab

By the time you have completed this lab, you should be able to

* Add a new method to declaration of a simple C++ class
* Add implementation of a new method to a simple C++ class definition
* Test a simple C++ class implementation
* Continue practicing with pre-written Makefiles


# Step by Step Instructions

## Step 1: Getting Ready

1. Go to github and find a repo for this lab assigned to your GitHub id.

2. Log on to your CSIL account.

3. Change into your `~/cs16` directory

4. Clone your empty {{page.num}} repo into your `~/cs16` directory.

5. In your empty repo, do `git checkout -b main` to establish that you are on the `main` branch as your default branch.


## Step 2: Obtain the starter code

The starter code is in this repo:

* <https://github.com/{{site.github_org}}/STARTER-{{page.num}}>

The URL for cloning this repo is this: `git@github.com:{{site.github_org}}/STARTER-{{page.num}}.git`

Previous labs contain instruction for the process of:
* Adding a `starter` remote for this repo
* Pulling the code from that `starter` remote into your own repo.

Please do those steps now, and then do a `git push origin main` to populate your own repo with the starter code.

If you need help with these steps:
* First consult previous labs for more detailed instructions.   
* Then, if you are still having trouble, ask the staff for help during discussion section or office hours.

Once you've populated your repo, typing the `ls` command should show you the following files in your current directory

```
$ ls
Makefile	Rectangle.cpp	Rectangle.h	rugfit1.cpp	rugfit2.cpp
$ 
```



## Step 3: Study a non-OO program

In the rest of this lab, you will finish writing a C++ program that uses an object-oriented (OO) approach to solve exactly the same problems that are solved by rugfit1.cpp - but first study this program to understand the problems and their non-OO solutions:

* After including the standard C++ input-output library, a utility function is defined for calculating the area of a rectangle. All other work is done inside the main function.
* All variables are declared at the beginning of main.
* The user is prompted to enter data, and the data are read into the appropriate variables.
* Calculations are performed using the area function to help.
* Results are printed.

Here is a sample run of the program :

```
-bash-4.3$ ./rugfit1
enter width and length of floor: 10.5 15
enter width and length of rug: 13.2 7.9
floor area: 157.5
rug area: 104.28
leftover rug area: 0
empty floor area: 53.22
```

Your revision of this program should operate exactly the same way. You will make the revision using the provided skeleton code in rugfit2.cpp

## Step 4: Know what it means to design an OO program

An experienced OO programmer would frown at the sight of variable names like `floorWidth` and `floorLength`, and would absolutely cringe at seeing names like `rugWidth` and `rugLength`. Such a programmer's object-oriented training would scream out the need for objects named `floor` and `rug` each of type `Rectangle` each with its own `width` and `length` attributes. 

And although this programmer would appreciate the procedural abstraction of an `area` function, they would prefer to let the `floor` and `rug` objects calculate their own areas. In response, the OO programmer probably would decide to write a class that can represent either a floor or a rug, or any other rectangle for that matter. Then he would use objects of this class to solve problems - maybe even future problems the programmer is not facing yet.

Here are the steps necessary to achieve such an object-oriented solution:

* Write a class definition for class `Rectangle`. This definition includes declarations for private instance variables to store a width and a height, and declarations for public methods that can be used by programs that need Rectangle objects. This class is the abstraction (the ADT).  You can see such a definition in the file `Rectangle.h`; it lacks only an implementation of the `area` method.

* Define (a.k.a. implement) the methods of class `Rectangle` that were only declared in the class definition. These method definitions use a special syntax that includes a "scope resolution operator" (::) to tie them to the Rectangle class. These methods implement the abstraction.  These can be found in the file `Rectangle.cpp` (again, except for the `area` method.)

* Create and use `Rectangle` objects to solve problems, often just in a `main()` function. This `main()` function applies the abstraction.

* Discuss the meaning of these steps with someone else in your discussion section, to make sure you both understand (at least generally) what you are to do, and hopefully gain an appreciation for why you might want to do it that way.

## Step 5: Complete the OO solution

First you should study the parts of 
* (1) the abstraction, where class `Rectangle` is defined in `Rectangle.h`,
* (2) the implementation, where the methods of class `Rectangle` are defined (a.k.a. implemented) in `Rectangle.cpp` 
* (3) the application, where the main function is defined, and the abstraction and its implementation are used, in `rugfit2.cpp`

Your job involves additions to each of these parts.

(1) In `Rectangle.h`, i.e. the definition of class Rectangle: declare a function named area that will take no arguments and will return a double value. Make the function const - meaning it promises not to change the object on which it is called - just like the getWidth and getLength functions that are already declared in the skeleton.

(2) In `Rectangle.cpp`, scroll past the existing definitions of the constructor and four standard get and set methods, and then define the `area` method you declared above. Look at the other method definitions as examples for how to do it - notice they use the scope resolution operator `::` to identify their connection to a particular class, as in `Rectangle::setLength` which identifies it as pertaining to class `Rectangle`. The `area` method should return the value of `length` times `width`.

(3) In the `main()` function: prompt the user for the width and length of the rug, read those two values from the user, and then reset the width and length of the `Rectangle` object named rug with the user's dimensions (using the rug's `setWidth` and `setLength` methods, of course). As a reminder, you use the object's name, the dot operator, and the name of the method to do such things. For example, if we wanted to find the value of the floor's width, we could do so by using the getWidth method as follows:
`floor.getWidth()`

(4) Also in main: change the two assignment statements for `floorArea` and `rugArea` to use the `area` method for each of the floor and rug objects.

## Step 6: Compile and run the program to test it

Use make to compile your program. Then run it to make sure everything works.  Here is a test of our solution:

```
-bash-4.3$ make rugfit2
clang++ rugfit2.cpp -c
clang++ Rectangle.cpp -c
clang++ rugfit2.o Rectangle.o -o rugfit2
-bash-4.3$ ./rugfit2
enter width and length of floor: 10 11.5
enter width and length of rug: 8 15
floor area: 115
rug area: 120
leftover rug area: 5
empty floor area: 0
```

If errors occur: read the error messages and try to figure out what needs changing. Don't just randomly make changes, but instead really think about the problem and how to fix it.

## Step 7: Upload your code to github one last time

Hopefully you remembered to sync your local changes to github often as you were completing the assignment.

If you forgot to do so, be sure to follow the steps in section 1d (above) to upload your final code to github


## Step 8: Submit your code to gradescope

Go to our class site on [www.gradescope.com](www.gradescope.com). Navigate to the assignment for this lab and submit your code via github.

You should see a score of 100/100 for this lab.

