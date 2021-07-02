---
title: "Using Linux"
tags: [linux]
keywords: linux
last_updated: July 2, 2018
sidebar: tutorials
permalink: using_linux.html
---

## Getting to a Terminal

1. Click on the 3x3 formation of dots in the lower left-hand corner.

2. Type in "terminal."

3. A terminal window will open.

## Changing Windows

* This is similar to operating systems such as Windows and Mac OS. Hit alt-tab to cycle windows, or click on the icons on the launcher.


## Locking Frequently-Used Programs to the Launcher

1. Right-click on the application that you would like to lock to the launcher.

2. Click "Lock to Launcher."


## Basic Linux Commands

Here a few commands you will need during the course of this camp. Try them out.

Command | Example | What it does
------- | ------- | ------------
ls | `ls .` | Lists the contents of the current directory.
mkdir | `mkdir new` | Makes a directory.
cd | `cd new` | Enters a different directory.
pwd | `pwd` | Tells you what directory you are in. "Present Working Directory"

When you first open the terminal you will see a command prompt. You will be in your home directory. If you type pwd, you will see the "path" to your home directory.

The path given to you by pwd is called an "absolute path." If you type an absolute path anywhere in the system, it will always refer to the same place. Absolute paths begin with "/".

A relative path is any path that does not begin with "/". Relative paths are stated relative to your present working directory. If you type "cd ex01" from your home directory, it will go to the directory "ex01" inside your home directory.

Here are a few shortcuts that you can use when forming paths.

 Shortcut | Meaning | Detail 
 ------- | ------- | ------
 ~     | Home directory.            | A space set aside for each user to store their files. 
 .     | The current directory.     |                                                       
 ..    | The parent directory.      |                                                       
 /     | The root directory.        | The very top of the computer's filesystem.            

Here's a quick exercise to try this all out.

1. mkdir linux_exercise

2. ls

3. cd linux_exercise

4. ls ..

5. cd ..

6. ls

7. mkdir linux_exercise/subdirectory

8. cd ~/linux_exercise/subdirectory

9. pwd

10. cd ~

This is basically a text-based version of double clicking on folders, but the command line is a powerful tool which you will use all week.

## Tab Completion

The command line has tab-completion. If you start typing the name of a file, directory, or command and hit tab, it will finish the name for you. If there is more than one match, all possible options are displayed.

## Text Editor

For the C++ tutorials, we will use a text editor called Sublime.

To open Sublime you can do one of two things:

* Open a terminal, type "sublime_text &", hit Enter. The & tells the computer to allow you to continue to use that terminal while the editor is running.

* Open the lens (the dots) as before, type in sublime_text, hit Enter. You do not need the & in the lens.

Using sublime and the command line, you will write and execute your tutorial programs.

## Arduino IDE

The robot uses an Arduino microcontroller. For programming the robot, we will use the Arduino IDE (Integrated Development Environment).

Opening arduino is the same as opening Sublime, except that you will type "arduino" in either the terminal or the lens.

## Logging Out

Before you leave the lab, make sure you save all your work and log out of the computer so that it's free for the next person to use it. Open the account menu in the top right-hand corner of your screen and click log out.

{% include note.html content="Please do not reboot the computer. If you are experiencing technical difficulties, notify one of the camp staff."%}

## Next Step

Proceed to ["Cloning the Tutorials"](/cloning.html)
