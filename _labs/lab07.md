---
num: lab07
ready: true
desc: "Recursion"
assigned: 2023-03-01 13:00
due: 2023-03-17 23:59
---

# {{page.num}} - {{page.desc}}

## Goals of this lab

The goal of this lab is get more practice with recursion, linked-lists, and string functions. 

To prepare you for the final exam, this lab will ask you to implement functions that may appear difficult. Do not panic! 

First, refer to this following problem solving guide and follow the guidelines to help you solve complex problems:

* <https://ucsb-cs16.github.io/w23/assets/pdfs/alexmei-problem-solving.pdf>. 

If you need more assistance, the course staff is happy to provide you additional support on Piazza, in section, and during office hours.

Continue to practice code tracing to reason about your code. We request that you DO NOT ask the staff to debug your code. They have been specifically instructed not to debug for you, rather to guide in the process. 

Do not refer the starter code from previous offerings of this course as this version is new. Remember that code that is not written by you (even if it from starter code from a previous offering) is in violation of the academic honesty for this class.

# Step by Step Instructions!

## Step 1: Getting Started

1. Go to github and find a repo for this lab assigned to your GitHub id.
2. Log on to your CSIL account.
3. Change into your `~/cs16` directory
4. Clone your empty {{page.num}} repo into your `~/cs16` directory.
5. In your empty repo, do `git checkout -b main` to establish that you are on the `main` branch as your default branch.

Note: Remember to push your work to github at the end of EVERY work session. That way, you will not accidentally lose your code.

## Step 2: Starter Code

* <https://github.com/{{site.github_org}}/STARTER-{{page.num}}>

The URL for cloning this repo is this:

*  <tt>git@github.com:{{site.github_org}}/STARTER-{{page.num}}.git</tt>

Previous labs contain instruction for the process of:
* Adding a `starter` remote for this repo
* Pulling the code from that `starter` remote into your own repo.

Please do those steps now, and then do a `git push origin main` to populate your own repo with the starter code.

If you need help with these steps:
* First consult previous labs for more detailed instructions.   
* Then, if you are still having trouble, ask the staff for help during discussion section or office hours.

Once you've populated your repo, typing the `ls` command should show you the following files in your current directory.

```
$ ls
deleteKthNodeTest.cpp   linkedListFuncs.cpp  removeKFromFrontTest.cpp  strTest.cpp
elementwiseSumTest.cpp  linkedListFuncs.h    spliceTest.cpp            sumTest.cpp
findKthNodeTest.cpp     Makefile             strFuncs.cpp              tddFuncs.cpp
largestValueTest.cpp    README.md            strFuncs.h                tddFuncs.h
```

## Step 3: Review the Files

Here is a list of your tasks for this lab:

### Step 3a: Look at the Big Picture

Type "make tests" and you will see some tests pass, but some fail. 

You are finished when all the tests pass. You will need to edit two files: <code>linkedListFuncs.cpp</code> and <code>strFuncs.cpp</code>

Please note that this lab may be more difficult than the previous labs you have worked on. We encourage you to ask questions publicly on Piazza (so your classmates can be of assistance) and attend office hours for 1:1 assistance.

### Step 3b: String and Linked List and Functions

Please note that all of these functions **must** be written recursively. You will not get credit if you implement them iteratively.
There are 8 functions you will need to write for this lab, one of which is a bonus:

In strFuncs.cpp:
- **[10 points] isPalindrome()**
  - Recursively check if a string is a palindrome
  - A palindrome is a word or phrase that reads the same backwards & forwards 
  - Palindromes **are not** case-sensitive - disregard spaces as well
  - Examples
    - *Noel sees Leon* reads *noeL sees leoN* backwards, and as we disregard spaces and capitalization, it is a palindrome
    - *HelloN* reads *olleH* and is not a palindrome
    
In linkedListFuncs.cpp:
- **[10 points] recursiveSum()**
   - Recursively calculate the sum of a linked list
   - Given a head node, return the sum of the linked list
   - Example
      - list:  2 &rarr; 3 &rarr; 4 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
        - recursiveSum(list) = 9

- **[10 points] recursiveLargestValue()**
   - Recursively find the largest value in a linked list
   - Given a head node, return the largest value in the linked list
   - Example
      - list:  2 &rarr; 3 &rarr; 4 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
        - recursiveLargestValue(list) = 4

- **[10 points] recursiveFindKthNode()**
  - Recursively find the kth Node of a linked list
  - Given a head node and integer k, return the address of the kth node
    - You do not know whether the linked-list contains k or more nodes; if k is greater than the length of the linked-list, return NULL
    - Example: 
      - list:  2 &rarr; 3 &rarr; 4 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
        - recursiveFindKthNode(list, 1) = 2
        - recursiveFindKthNode(list, 3) = 4
        - recursiveFindKthNode(list, 4) = NULL

- **[10 points] recursiveDeleteKthNode()**
  - Recursively delete the kth node from a linked list 
  - Given the head of a linked list, delete the kth node from the linked list
    - k will always be less than or equal to the length of the linked list
    - Return NULL if there are no nodes left after deleting.
  - Example: 
      - list:  2 &rarr; 3 &rarr; 4 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
        - recursiveDeleteKthNode(list, 2) = 2 &rarr; 4
        - recursiveDeleteKthNode(list, 1) = 3 &rarr; 4
        - recursiveDeleteKthNode(list, 4) = 2 &rarr; 3

- **[10 points] recursiveRemoveKFromFront()**
  - Recursively delete k nodes from a linked list
  - Given the head of a linked list, delete the first k nodes from the linked list
    - k will always be less than or equal to the length of the linked list
    - Return NULL if there are no nodes left after deleting.
  - Example: 
      - list:  2 &rarr; 3 &rarr; 4 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
        - recursiveRemoveKFromFront(list, 2) = 4
        - recursiveRemoveKFromFront(list, 1) = 3 &rarr; 4

- **[20 points] recursiveElementwiseSum()**
  - Recursively find the elementwise sum of two linked lists
  - Given two head nodes, return the head of a **new** linked-list where each element is the sum of the corresponding element of the other two
    - if one linked-list is shorter, fill the rest of the result with elements from the other (i.e., treat the non-existent nodes as a value of zero)
    - Do **NOT** change the values of the original linked list - you must make a new one
    - Examples
      - Linked List 1: 1 &rarr; 2 &rarr; 3 &rarr; 4 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Linked List 2: 5 &rarr; 6 &rarr; 7 
        - Output: 6 &rarr; 8 &rarr; 10 &rarr; 4 

- **[BONUS: 1% Extra Credit] recursiveSplice()**
  - This is a bonus problem; doing it is optional
  - Recursively splice together two linked lists
  - Given two linked lists, splice the two linked lists together
    - Splice two linked lists by interweaving the nodes - the second linked list's nodes should be inserted at alternating positions into the first linked list
    - If the size of the two linked lists differ, after successfully splicing, finish the combined linked list with the remaining elements of the larger linked list
   - Examples
      - Linked List 1: 1 &rarr; 2 &rarr; 3 &rarr; 4 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Linked List 2: 5 &rarr; 6 &rarr; 7 &rarr; 8 
        - Output: 1 &rarr; 5 &rarr; 2 &rarr; 6 &rarr; 3 &rarr; 7 &rarr; 4 &rarr; 8

      - Linked List 1: 1 &rarr; 2 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Linked List 2: 3 &rarr; 4 &rarr; 5 &rarr; 6
        - Output: 1 &rarr; 3 &rarr; 2 &rarr; 4 &rarr; 5 &rarr; 6 
        
  - You CANNOT create another linked list - doing so will fail both the local tests and Gradescope tests. Instead, splice the lists together by rearranging the *next* pointers of each linked list. You are allowed to declare additional nodes, but the returned linked list should only contain nodes from each linked list, in some order. 
  
Each one has a set of tests which can be found under its corresponding heading when you type <code>make tests</code>. For example, the recursiveRemoveKNodesFromFront tests look like this to start: 

```
./llTests 1
--------------REMOVE_K_NODES_FROM_THE_FRONT_OF_THE_LIST--------------
   FAILED: Remove 3 from front of 1->2->3->4->5
     Expected: 4 5  Actual:
```

You should replace each function stub with the correct code for the function until all of the tests for each one pass. It is recommended that you work on the functions one at a time in the order that they are presented above. That is, get all the tests to pass for isPalindrome then recursiveSum and so on. When all the tests pass, move on to the next step. **Note that the test cases provided to you in the lab are not comprehensive. Think about possible edge cases that is breaking your code.**

## Step 4: Check Your Work

When you are finished, you should be able to type  <code>make clean</code> and then <code>make tests</code> and see all of the tests pass.

At that point, you are ready to try submitting on gradescope. 


## Step 5: Submitting on Gradescope

Submit the `strFuncs.cpp` and `linkedListFuncs.cpp` files on gradescope. 

**If your code does not pass the Gradescope tests, think about possible edge cases that is breaking your code.**

# Grading Rubric

Most of the points will be awarded based on gradescope automatic grading. Other points will be assigned after visual code inspection by TAs - if a function is not implemented recursively, you will receive **NOT** receive any credit for that function at all.

The *recursiveSplice* function is a bonus question - note that it is intended to be difficult. Although Gradescope will be display a score out of 110, your lab is only worth 100 points - should you successfully complete the bonus and the rest of the lab, you will receive 100/100 on the lab and 1% extra credit in the course. We will manually adjust the grades afterwards.

## Gradescope Autograder

<table border="1">
<tr><th>Test Name</th><th>Value</th></tr>
<tr><td><p style="color:green;margin:0;padding:0;">isPalindrome()</p></td><td>[10 pts]</td></tr>
<tr><td><p style="color:green;margin:0;padding:0;">recursiveSum()</p></td><td>[10 pts]</td></tr>
<tr><td><p style="color:green;margin:0;padding:0;">recursiveLargestValue()</p></td><td>[10 pts]</td></tr>
<tr><td><p style="color:green;margin:0;padding:0;">recursiveFindKthNode()</p></td><td>[10 pts]</td></tr>
<tr><td><p style="color:green;margin:0;padding:0;">recursiveDeleteKthNode()</p></td><td>[10 pts]</td></tr>
<tr><td><p style="color:green;margin:0;padding:0;">recursiveRemoveKFromFront()</p></td><td>[10 pts]</td></tr>
<tr><td><p style="color:green;margin:0;padding:0;">recursiveElementwiseSum()</p></td><td>[20 pts]</td></tr>
<tr><td><p style="color:green;margin:0;padding:0;">recursiveSplice()</p></td><td>[1% Course Extra Credit]</td></tr>
</table>

## Manual Grading

* **Recursive Implementations:**
1. You will receive NO credit for any function you did not implement using recursion. The points you receive from the autograder will be deducted from your final score.
* **[20 pts] Code Comments and Coding Style:**
1. Code Comments: comments are clear and descriptive, making the code easy to understand; the comments should be convincing that the student understands the code they've written.
2. Code Style: code can be easily understood by humans familiar with C++; code is neatly indented and formatted; variable names choices are reasonable; code is reasonably "DRY" (as in "don't repeat yourself")&mdash;where appropriate, common code is factored out into functions; code is not unnecessarily or unreasonably complex when a simpler solution is available.

** If your comments or coding style is exceptionally underwhelming, you will not receive any of these points **

Refer to the following style guide to learn more about good coding style: [link to style guide](https://docs.google.com/presentation/d/16ExuzjlRWClQe-GbX_FNYKsSJnrd0Z5ef7N1c0sezUA/edit?usp=sharing). If you are unsure about the quality of your code and comments, please ask a member of the course staff during section or office hours. 

## Academic Honesty

We will test your code against other data files too&mdash;not just these. So while you might be able to pass the tests on gradescope now by just doing a hard-coded "cout" of the expected output, that will NOT receive credit.    

To be very clear, code like this will pass on gradescope, but represents a form of academic dishonesty since it is an attempt to just "game the system", i.e. to get the tests to pass without really solving the problem.

I would hope this would be obvious, but I have to say it so that there is no ambiguity: hard coding your output is a form of cheating, i.e. a form of "academic dishonesty".  Submitting a program of this kind would be subject not only to a reduced grade, but to possible disciplinary penalties.    If there is <em>any</em> doubt about this fact, please ask your TA and/or your instructor for clarification.

And, as usual, all code you submit must be written and thought of by you. Referring to online homework answer services is definitely a form of academic dishonesty and will be reported. Do not jeopardize your academic career over one assignment. Please reach out on Piazza and come to section or office hours if you need help.

## Logging Out

If you are logged in remotely, you can log out using the exit command:

```
$ exit
```
