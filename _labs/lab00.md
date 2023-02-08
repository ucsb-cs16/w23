---
num: lab00
ready: true
desc: "Submitting to Gradescope"
assigned: 2023-02-08 13:00
due: 2023-02-14 23:59
---

# {{page.num}}: {{page.desc}}

## Introduction

This week's lab is design to help you learn about you CSIL/ECI/CoE account, GitHub and Gradescope, three important tools you'll use in this course and that may be used in future CMPSC courses you may take at UCSB.

# Part 1: Get setup with the tools for this course

I've tried to parcel out these set up steps over several small assignments before we got to this point, so we can hope that
you've already done everything in Part 1.  But go through the steps to check.

## Step 1: Add yourself to the GitHub organization

You should have already done this; it's described in the zyBook here:

* <https://learn.zybooks.com/zybook/UCSBCMPSC16Winter2022/chapter/5/section/14>

But if not, please do it now.

## Step 2: Create a CoE (ECI/CSIL) account if you don't have one already

You should have already done this; it's described in the zyBook here:

* <https://learn.zybooks.com/zybook/UCSBCMPSC16Winter2022/chapter/5/section/15>

But if not, please do it now.


## Step 3: Check that you are in the GitHub Org and have a `lab00-YOUR-GITHUB-USERNAME` repo.

In order to continue with the lab, you need to be a member of the GitHub organization, and you need to have a lab00 repo.

* Bring up the web page: <https://github.com> and login to your GitHub account.
* Then, in the same browser window, navigate to <https://github.com/ucsb-cs16-w23>.   Then go to the tab that says `People`, and under that tab, search for your own name (or GitHub id).  You should be able to see the members of the organization, and your name should appear in that list.
  * If you are not able to see the `People` tab, or your name does not appear in the list, look at the top of the page for <https://github.com/ucsb-cs16-w23> and see if you find an invitation to the organization that you haven't accepted yet.  If that appears, please click to accept the invitation to the organization.  After doing this, one of the staff will need to create your lab02 repository, so ask for assistance.
* Assuming you got this far, look under the tab for repositories.  You should see a listing for a repository called `lab00-YOUR-GITHUB-USERNAME` where `YOUR-GITHUB-USERNAME` is your GitHub username (for example `lab00-cgaucho`).
  * If you don't see a `lab00-YOUR-GITHUB-USERNAME` repo, then ask a staff member for assistance.

## Step 4: Get setup with gradescope

We will use gradescope to grade all your homeworks, exams and lab/programming assignments. I have manually added everyone (using your @umail.ucsb.edu accounts) 
currently enrolled in the course to the Gradescope system. 
You should have received an email notification with instructions about logging into gradescope. 
Once you follow the instructions to set your password, you should have access to our course on Gradescope. 

* You should see "CMPSC 16" in your courses for this quarter.
* The lab assignment `lab00` should appear in your Gradescope dashboard under CMPSC 16.  You'll be submitting your assignment using Gradescope this week.

If you don't have `CMPSC 16` and `lab00` on Gradescope, please contact the staff for assistance.

That's it for preliminaries!   If everything above is sorted, we're ready to get started.

# Part 2: Clone a github repo, add a simple C++ program, submit on Gradescope

## Step 5: Open a Terminal on CSIL 

In this assignment, we'll be working on your CSIL/ECI/CoE to:
* clone a GitHub repo
* edit and compile a simple C++ program
* add that C++ program to your repo
* submit it to Gradescope for grading

The first step in every assignment where you work on CSIL/ECI/CoE is to open a <b>terminal window on CSIL</b>.

* If you are working on a desktop machine in Phelps 3525, this is super easy; open a terminal window, and you are there. 
* If you are working on your own machine:
  - Windows: You can use Powershell 
  - MacOS: You can use Terminal
  - Linux/Unix: Any terminal shell
  
The command to open a terminal on CSIL is this, where `USERNAME` is your CSIL/ECI/CoE username (e.g. the one you created at <https://accounts.engr.ucsb.edu>:
  
```
$ ssh USERNAME@csil.cs.ucsb.edu
```

The name `csil.cs.ucsb.edu` is actually a "front end" to a collection of machines with names such as these:
* `csilvm-01.cs.ucsb.edu`
* `csilvm-02.cs.ucsb.edu`
* etc.

The system will choose one of these for you (to try to spread the load over multiple machines), and then connect you to it.

The first time you connect to a particular machine, ssh may first ask you a question which looks like this

```
The authenticity of host 'csil.cs.ucsb.edu (128.111.43.14)' can't be established.
RSA key fingerprint is 90:ab:6a:31:0b:81:62:25:9b:11:50:05:18:d3:1a:b5.
Are you sure you want to continue connecting (yes/no)?
```

Please answer `yes`, and after that you won't see this message again. (This adds a line into the file `~/.ssh/known_hosts` for `csil.cs.ucsb.edu`, where `~` is the home directory on the computer from which you are connecting.)

It will next ask for your CoE/CSIL/ECI account password. When you type it in, nothing will show on the screen (not even dots). However what you type is still being sent and once you are finished with your password, you can press ENTER to login.

<b>You should now be remotely connected to CSIL!</b> You can make sure by typing the following command (which will tell you what machine you are currently issuing commands to):

```
$ hostname

```

This should show the name of one of the virtual machines such as `csilvm-01.cs.ucsb.edu`. You can now do anything you could normally do in a terminal window in CSIL or the Phelps lab, with the exception of programs that use graphics.

Note: While it isn't required for this lab, if you are interested in running programs that use graphics, you can use something called
the Remote Desktop Protcol (RDP), which is explained in [this article](https://ucsb-engr.atlassian.net/wiki/spaces/EPK/pages/602046589/Remote+Access+to+ECI+Computing+Labs).   But I suggest that you skip over that for now, and just continue with the rest of this lab.  We'll return to RDP as and when it's needed for something in this course.


## Step 6: Set up git and ssh keys on CSIL

There are two pieces of "one time setup" that you need to do in order
to configure your CSIL account to work with git/github:

* <https://ucsb-cs16.github.io/topics/git_csil_configuration>
* <https://ucsb-cs16.github.io/topics/github_ssh_keys>

You should only need to do this once (not even once per course, but once for all time for your CSIL account.)


## Step 7: Create cs16 directory

Now that your environment is set up, you will need to create a directory (a folder is also called <i>directory</i> in Linux) that will contain all your work for the course. Then, inside that directory, you will need to create another directory to contain your work for this assignment.

To create your CS16 directory, use the <b>mkdir</b> command. Type the following in the terminal and press enter:

```
$ mkdir cs16
```

The <b>$</b> represents the terminal prompt; <i>you won't type this character</i>. Whenever you see it, that means that the following command is intended to be typed into the terminal window and run by pressing enter.

You can see list of files and directories in the current directory with <b>ls</b> command. Type the following in the terminal and press enter:

```
$ ls
```

You should be able to see the directory you just created i.e. **cs16**

Now move into that new cs16 directory with the <b>cd</b> command as follows:

```
$ cd cs16
```

You should now be able to type `pwd` and see that you are in your `cs16` directory under your home directory, e.g.

```
$ pwd
/cs/student/cgaucho/cs16
$
```

## Step 8: Clone your lab00 repo

Next, open a web browser to <https://github.com/ucsb-cs16-w23> and if you are not already logged in, login to GitHub.

Under the repositories tab, you should see a repo called `lab00-YOUR-GITHUB-USERNAME`, for example `lab00-cgaucho`.

Navigate to the page for this repo.  The URL will be something like this: 
* <https://github.com/ucsb-cs16-w23/lab00-cgaucho>

On that page, you'll see something like this (in this image, the user is `Avishek-De`, one of the TAs for CS16 in F21.  In your case,
the text `Avishek-De` should be replaced with your GitHub id.)

![image](https://user-images.githubusercontent.com/1119017/137171006-e35db304-04a3-487e-b9d0-8042783c757e.png)

As you can see, there are two buttons, labelled HTTPS and SSH.  Try clicking on the HTTPS and SSH buttons and see what happens.  You'll notice that the URL changes between two formats, as shown in the table below.

| When you click this button | Then the URL should look like this | Which one do we want? |
|----------------------------|------------------------------------|-----------------------|
| `HTTPS` | `https://github.com/ucsb-cs16-w23/lab00-AvishekDe.git` | <span>NOT this</span>{: .label .label-red } | 
| `SSH`   |  `git@github.com:ucsb-cs16-w23/lab00-AvishekDe.git` | <span>THIS</span>{: .label .label-green }  |

Be sure that you click the SSH button and that your URL starts with `git@github.com` and ends with `lab00-YOUR-GITHUB-USERNAME` (e.g. `lab00-cgaucho`) before proceeding.

Next, copy the URL that starts with `git@github.com` from the box.  We are going to type `git clone` at the command line (still inside your `cs16` directory) and then paste this URL, so that command looks like this:

```
$ git clone git@github.com:ucsb-cs16-w23/lab00-YOUR-GITHUB-USERNAME.git
```

The first time you connect, you might see output like this (it may not look precisely the same, but similar):

```
The authenticity of host 'github.com (140.82.113.4)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:2: 192.30.255.113
    ~/.ssh/known_hosts:5: 140.82.113.4
    ~/.ssh/known_hosts:6: 140.82.112.3
    ~/.ssh/known_hosts:7: 140.82.114.3
    ~/.ssh/known_hosts:8: 140.82.113.3
    ~/.ssh/known_hosts:10: 140.82.112.4
    ~/.ssh/known_hosts:11: 140.82.114.4
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
```

Please answer `yes`, and after that you won't see this message again. (This adds a line into the file `~/.ssh/known_hosts` for `github.com`, this time, in your CSIL/ECI/CoE account's home directory.)

After you do that, you should see output such as this:

```
[pconrad@csilvm-03 cs16]$ git clone git@github.com:ucsb-cs16-w23/lab00-YOUR-GITHUB-ID
Cloning into 'lab00-YOUR-GITHUB-ID'...
warning: You appear to have cloned an empty repository.
```

You should now be able to type `ls` and see that inside your `cs16` directory, there is a directory called `lab00-YOUR-GITHUB-ID`.

To move into this directory, please type:

```
$ cd lab00-YOUR-GITHUB-ID
```

Once you do, if you type `pwd`, you should see output such as this (but with your ECI account id in place of `chrisgaucho`, and your GitHub id in place of `cgaucho`):

```
$ pwd
/cs/student/chrisgaucho/cs16/lab00-cgaucho
$ 
```

If you type `ls` at this point, it should appear to be an empty directory:

```
$ ls
$ 
```

However, if you type `ls -a`, you'll see that there are listings for  `.`, `..` and a directory called `.git`:

```
$ ls -a
.  ..  .git
$ 
```

Each of these is normally *hidden* because the name starts with a dot (`.`).  We add `-a` to the `ls` command to see
hidden files.   The hidden folder/directory `.git` is what distinguishes a regular plain old folder/directory from one
that is a *git repository*.   The various versions of our program are stored inside the `.git` folder, along with other
data that `git` uses to keep track of information about the repository.  

For now, and unless/until you know what you are 
doing with `git` internals, it is best to leave the contents of the `.git` directory alone; we manipulate the information
inside `.git` using git commands.

Now that we have an empty repository (i.e. an empty directory, apart from the `.git` directory), we are ready to create
a C++ program in this repository.  From here on out, we'll use the word *repo* as short for *repository* (they mean the same thing.)

As an aside; knowing how to navigate a UNIX environment and issue UNIX commands is VERY valuable to computer scientists and engineers, especially when working with cloud computing, which is an increasing part of how work in our field gets done.  To learn more UNIX commands, there are lot of cool Web resources and books on the topic. This is one website with a good introductory page: [Useful unix commands](http://mally.stanford.edu/~sr/computing/basic-unix.html).

## Step 9: Editing text files for programming <a name="step4"></a>

Let's take a little detour on how to best create and modify text files. These will carry all the code (regardless of computer language) that we want to assemble, compile, and execute.

You are likely familiar with Microsoft Word as a widely-used "word processor", but please DO <b>NOT</b> USE MS WORD TO WRITE PROGRAMS!!!

Instead, for programming, you have access to a very large number of excellent text editors&mdash;and most of them are free to use! All software developers have their preferences, but learning the basics of a Unix-based command line text editor is very important. Every student who intends to study computer science should learn a popular Unix-based text editor (such as vim or emacs), since it is not uncommon that the machine you need to work on does not have a Graphical User Interface (GUI), and you may be forced to use a command-line editor. 

The two most popular Unix-based command line editors are <b>vim</b> and <b>emacs</b>.   Some developers tend to get a little passionate about text editors, and will endlessly argue the benefits of vim over emacs, or emacs over vim.  But it is widely acknowledged even among <b>emacs</b> fans then <b>vim</b> has this advantage over <b>emacs</b>: it is more widely available, i.e.
it tends to be installed by default on most Unix-based systems, while <b>emacs</b> is a separate install.  

Three of the CS instructors (Professors Diba Mirza, Richert Wang, and Phill Conrad) did an very informal survey of a number of UCSB CS alums working in the software industry, and the consensus was this: students should learn:
* Enough `vim` to be able to make simple edits to files
* Then transition to an open source, full-fledged editor with IDE type features, VS Code being the leading contender.

Therefore, in this class:
* For the first couple labs in this class, we will be using <b>vim</b> to work on our programs.
* We'll then show you how you can transition to VS Code if you like.

Ultimately, the choice of text editor is a personal one, and if you are already familiar with an editor you prefer (e.g. Atom, XCode, Eclipse, etc.) it's perfectly fine for you to continue using that editor, though we will expect every CS16 student to develop at least
*basic* profciency with vim.   We have a list of eight things you need to know how to do in vim in this article:

* <https://ucsb-cs16.github.io/topics/vim_basic_eight.html>

## <b>vim</b> for UNIX-based OS

vim (or sometimes called vi) is a popular editor that's also available on just about every UNIX machine (including the ones that you're using in the CS labs) and UNIX-based machines (like MacOS computers).

To create or make changes to a file (let's say it's called "filename.cpp"), you'd type the following at the prompt. (Throughout these instructions, the `$` represents the command line prompt, and is not part of the command you type.)

```
	$ vim filename.cpp
```

If you want to practice creating a file in vim, you can do so in the `lab00-YOUR-USERNAME-HERE` directory.   You can remove files
that you no longer want (e.g. ones you create for practice), with the `rm` command, e.g.

```
$ rm filename.cpp
```

Try creating a file called `filename.cpp` with vim, and then deleting it with `rm filename.cpp` as you work through the
vim instructions below.  (The contents of `filename.cpp` don't really matter for now, since it's just for practice; you can
type C++ code, or a shopping list, or anything you like.)

### What do we need to know about vim for CS16?

While we stress that ultimately the choice of text editor is a personal choice, that we leave up to you, we do want every CS16 student to at the very least develop basic vim skills for a minimal set of commands, which we call the "basic eight".

Those are documented here: 
* <https://ucsb-cs16.github.io/topics/vim_basic_eight/>

There may be an assignment later this quarter where you need to do a live demo for one of the TAs or LAs demonstrating that you know these basic eight skills in vim.


### Brief overview of vim

Even if you are already getting comfortable with vim, please read through the following.  It may help give you some vocabulary to talk about `vim`, and also help you get more comfortable with how `vim` works.

The most important things to know about vim is that `vim` has various modes, including "normal" mode, `INSERT` mode, and "command" mode.
* In "normal" mode, each key on your keyboard may do some editor command.
* In `INSERT` mode, you see `INSERT` at the bottom of the screen.  This is the mode in which you type in text, use the arrow keys, and can use the delete key to delete the characters immediately before the cursor.
* In "command" mode, the cursor jumps to the bottom of the screen, and you see a colon `:` where you can type commands.

How do you move between modes?
* To move from normal mode into insert mode: type the letter `i`.  You should see `INSERT` appear at the bottom of the screen.
* To move from insert mode back to normal mode: press the "escape" key (usually labelled `esc`, and at the top left of your keyboard).  The word `INSERT` should disappear.
* To move from normal mode to command mode: type the colon, i.e. `:`.  The cursor shoudl jump to the bottom of the screen where you see a colon (`:`).  To get out of command mode, you type in a command (such as `w` to save the file, or `q` to quit) and press enter.  You can also just press enter by itself to get back to normal mode.

How do you enter text?
* You enter text by going into `INSERT` mode and just typing.  You can move the cursor around with the arrow keys.
* You can also use the delete key to remove text.

How do you do delete an entire line at once?
* To delete an entire line at once, go into "normal" mode (use the `esc` key to get out of `INSERT` mode), and then press the `d` key twice, i.e. type `dd`.   This should remove an entire line.
* If you want to put that line back, move your cursor up one line with the arrow key, and then press `p` to put the line back. (Note that `p` always puts the line back on the line below the cursor, so to undo the `dd` command, you need to move the cursor one line up first.)

How do you save the file?
* Get to normal mode (press `esc` if you in `INSERT` mode)
* Type `:` to go to command mode
* Use the `w` command ("write") to write out the file to the disk.

How do you save the file?
* Get to normal mode (press `esc` if you in `INSERT` mode)
* Type `:` to go to command mode
* Use the `q` command ("quit") to leave `vim`

Can you save and exit all at once?
* Yes.  Get to normal mode (press `esc` if you in `INSERT` mode)
* Type `:` to go to command mode
* Use the `wq` ("write", then quit") to leave `vim`

To learn more, including how to quit without saving, do search/replace, and copy/paste, see:  <https://ucsb-cs16.github.io/topics/vim_basic_eight/>


### More on vim

Again, to learn how to use vim, there is no substitute for PRACTICE!!! There are multiple online resources that you can look at and here are some of them:

* [About vim (from vim.org)](http://www.vim.org/about.php)
* [Vim "how to" from engadget.com](https://www.engadget.com/2012/07/10/vim-how-to/)
* [vim commands - a handy reference card](http://tnerual.eriogerg.free.fr/vimqrc.html)
* [another reference cheat sheet for vim](https://www.fprintf.net/vimCheatSheet.html)

In addition, there is the [Vim Adventures Game](https://vim-adventures.com/) that helps you learn vim while playing a video game.

## Step 10: Create and edit a file containing a C++ program

Now, in your `lab00-YOUR-USERNAME-HERE` directory, please create a single C++ program, following the steps below.

This assignment only needs you to write a program that prints out two lines on the display, and nothing else. <b>The output should look EXACTLY as follows</b> (no space before or after each line, except the 2 newlines):

```
Hello, world!
I am ready for CS16!
```

Start with a "skeleton program" (or template) that contains the necessary structure but that does not do anything:

```cpp
#include <iostream>

using namespace std;

int main() {
    // Your printing code should go here

    return 0;
}
```

Go ahead and type this in to the `hello.cpp` file. Alternatively, you can copy and paste it directly from this page.

Next, you will need to replace the comment with code to print out the expected output. Comments in C++ are lines that start with <b>//</b> or text between <b>/*</b> and <b>*/</b>. The second type can span multiple lines.

Important note: For students familiar with Python, remember that lines starting with the <b>#</b> character are not comments in C++. Rather, they are important `include` lines that allow your program to use the input and output functionality. Make sure to copy those lines in your program as well. Only `//` or `/* */` create comments in C++.

To print out text to the terminal, you can use the `cout` stream. To output something use the `<<` operator as shown below:</p>

```
cout << "This will be printed out to the terminal" << endl;
```

The `endl` stream manipulator will cause a newline (i.e. a carriage return) to be printed so that the next thing printed
goes on the next line.  

You can adapt this line to achieve the objective of the assignment. <b>Remember that we need to print two lines, each with a newline at the end.</b> You can do this with one or two statements.

## Step 11: Compile the Code 

Now that the code is written, we need to <em>compile</em> it. This will be done using a special program called a <em>compiler</em>.

Before moving on, <b>make sure you save your code</b> and close the text editor. The following step will be done in the terminal.

For C++ code we will use the <b>g++</b> compiler that's built into many UNIX machines (it even works on most MacOS terminal programs). You can compile the <b>hello.cpp</b> file into an executable called <b>hello</b> with the following command:

```
	$ g++ hello.cpp -o hello
```


This will compile your code and make an executable version of it. Specifically, it will tell the compiler to take the source code file <b>hello.cpp</b> and compile and link it to an executable called <b>hello</b>.

Alternatively, you can use this shortcut:

```
	$ make hello
```

The `make` program is a piece of software that helps you make software with C and C++.   It has automatic rules for generating compiler commands, one of which is that by default, to make an executable program called `hello`, the default compiler command is the one shown here.

Ultimately, you will need to know the long versions of the commands, but it's fine to use the shortcut for the time being.

If the compilation is successful, you won't see any output from the compiler, but if you issue a UNIX <b>ls</b> command, you should see a new file has appeared: one called <b>hello</b>. You can then use the following command to run your program:

```
	$ ./hello
```

Which means "in the current directory, as represented by the <b>.</b> character, run the program <b>hello</b>". You should then see the program output the two expected lines.

The other possibility is that the program may <b>not compile successfully</b>. What to do then?<br>
If you run the <b>g++</b> command and are unsuccesful with your compilation, then you might see an output that looks like this:

```
	hello.cpp: In function ‘int main()’:
	hello.cpp:10:1: error: expected ‘;’ before ‘}’ token
 	}
```

The compiler will try to give you hints on the line (in this case, it's complaining about line 10) where the error occurs, and also about what the error is (in this case a missing semicolon). You will also note that, in this case, an output executable file is not produced.

If you encounter an error, use the compiler hints and examine the line in question. If the compiler messsage is not sufficient to identify the error (which happens more than sometimes), you can search online to see when the error occurs in general. Once you have fixed the error, run the compilation command again. <i>Debugging</i> a program code is a necessary ritual in almost all programs written (even those written by expert coders). More on that in a later class.


## Step 12: Adding the file hello.cpp to your GitHub repo

In this step, we'll add the `hello.cpp` file to your GitHub repo.

This involves several steps, explained in the table below.  Try each step as you follow through the explanataion:

| Step | Command to type | What is happening |
|------|-----------------|-------------------|
| 0.   | `git checkout -b main`  | This creates a new branch called `main`.  This will be the only branch we use in this course.  For the time being, it's not necessary to know what a branch is; just know that we only use the branch called `main` |
| 1.   | `git add hello.cpp`. | This adds the file `hello.cpp` to something known as the *staging area*.  This prepares the file to be added to our git repo. |
| 2.   | `git status` | This command shows us the current status of our repo.  We should see that the file `hello.cpp` appears in green, as a file "to be committed". |
| 3.   | `git commit -m "add hello.cpp to repo"` | This commits the files in the staging area to the local repo on CSIL.  The `-m` stands for message, and the part in the quotes is the message.  Every commit has a message to our future selves and to other programmers about what we were doing when we made this commit.  Learning how to write good commit messages is an important skill. |
| 4.   | `git push origin main` |  This pushes the changes from our local repo on CSIL to the original repo that we cloned (i.e. `origin` on github.com |
{:.table .table-sm .table-striped .table-bordered}

Once you've gone through all of these steps, navigate to your repo on the web at this URL (but substituting in your userid in place of `YOUR-GITHUB-USERNAME`:
* <https://github.com/ucsb-cs16-w23/lab00-YOUR-GITHUB-USERNAME>

You should see a listing for the file `hello.cpp`, and if you click on it, you should see the entire contents of the file, something like this:

![image](https://user-images.githubusercontent.com/1119017/137179308-2a785c74-2605-41ae-b8ad-d70c85e5a870.png)

If you don't find that, go back through the instructions and see if there is a step you missed, or ask for assistance from the staff.

Once you see your code on GitHub, you are ready to try submitting on Gradescope.

## Step 13: Submitting your code to Gradescope
  
Now, login to your Gradescope account at <https://gradescope.com>.  I suggest using the `School Credentials` button as shown here (lower left button, above the `Remember Me` box.)

![image](https://user-images.githubusercontent.com/1119017/137179676-a9d78ff3-b2d0-4a64-8804-55176b7f86e6.png)

This brings up a long list of schools, as shown below.  Scroll down to `University of California Santa Barbara NetID`.  It isn't listed with `UC Davis`, `UC Santa Cruz` and `UCLA` but, for some reason, under the spelled out name `University of California`.

![image](https://user-images.githubusercontent.com/1119017/137179784-4fd4001f-39a8-47c1-ad58-e452030dff34.png)

![image](https://user-images.githubusercontent.com/1119017/137179880-cf0cc01b-1e31-49c2-b2cb-734408723894.png)

Once you login, you should find that CMPSC 16 is one of your courses.  If not, please contact the staff for assistance.

The lab assignment `lab00` should appear in your Gradescope dashboard. If you haven't submitted anything for this assignment yet, Gradescope will prompt you to upload your files.

You can do so in one of two ways:
* You can directly upload your file `hello.cpp`
* You can submit from your GitHub repo.

Once you submit something on Gradescope, it should take you to their "Autograder Results" page. There is a "Resubmit" button on the bottom right that will allow you to update files for your submission.

For this lab, if everything is correct, you'll see a successful submission passing all of the autograder tests and receive a 100/100.

Congratulations on completing your first C++ program!

## Step 14: If you don't get a 100% score on Gradescope

If instead, you see a problem, then read the error message and try to fix the problem.  You'll need to resubmit your file.    If/when you make changes, you should update the file on GitHub like this.  Note that this is the same list of steps as before, but without the step where we create the `main` branch (we only need to do that once.)

| Step | Command to type | What is happening |
|------|-----------------|-------------------|
| 1.   | `git add hello.cpp`. | This adds the file `hello.cpp` to something known as the *staging area*.  This prepares the file to be added to our git repo. |
| 2.   | `git status` | This command shows us the current status of our repo.  We should see that the file `hello.cpp` appears in green, as a file "to be committed". |
| 3.   | `git commit -m "add hello.cpp to repo"` | This commits the files in the staging area to the local repo on CSIL.  The `-m` stands for message, and the part in the quotes is the message.  Every commit has a message to our future selves and to other programmers about what we were doing when we made this commit.  Learning how to write good commit messages is an important skill. |
| 4.   | `git push origin main` |  This pushes the changes from our local repo on CSIL to the original repo that we cloned (i.e. `origin` on github.com |
{:.table .table-sm .table-striped .table-bordered}

Once you are finished, you can use the command `exit` or `logout` to close the terminal session on CSIL.

Congratulations on finishing your first lab involving ECI/CSIL/COE, GitHub, and Gradescope!
