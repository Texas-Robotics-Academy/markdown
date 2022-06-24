---
title: "Using Linux"
tags: [linux]
keywords: linux
sidebar: tutorials
permalink: using_linux.html
---

## Finding your Machine

With your partner and your box, go to the row labeled with your team number and names. You and your partner should each choose chairs at machines next to each other along your row.  Seat as ordered on your team chart. So, the person with the name at the top will go to the machine at the far end of the row, the second person will go to the machine next to them, and so forth.

## Introduction to Linux

The computers in this lab use the Linux operating system. Linux offers a variety of free easy-to-use tools for software development that will help us along our way in constructing and programming our robots.

### Logging In

1. Enter the user name given to you, and hit Enter.
2. On the next screen, first click on the gear and select "ubuntu" from the menu.
3. Type in the password assigned to you, hit Enter, and you should be taken to a desktop screen.
4. A box will pop up telling you about keyboard shortcuts. Click the X and move on to the interesting stuff.

### Getting to a Web Browser

By default, the Ubuntu logo will be displayed on the launcher to the left of the monitor in the upper left-hand corner.

1. Click on the Ubuntu logo icon. This will open the "lens".

2. Type in either "google-chrome" or "firefox" depending on which browser you would like to use.

   {% include note.html content="No, neither browser is better than the other for this camp. This is purely a matter of personal preference." %}

3. Go to <https://texas-robocamp.github.io/> to get to this site.

### Getting to a Terminal

1. Click on the Ubuntu logo icon.

2. Type in "terminal".

3. A terminal window will open.

### Changing Windows

This is similar to operating systems such as Windows and Mac OS. Hit alt-tab to cycle windows, or click on the icons on the launcher.


### Locking Frequently-Used Programs to the Launcher

1. Right-click on the application that you would like to lock to the launcher.

2. Click "Lock to Launcher."

### Basic Linux Commands

An important part of using Linux is becoming familiar with the command line. Here a few commands you will need during the course of this camp. Try them out.

Command | Example     | What it does
------- | ------------| ------------
ls      | `ls .`      | Lists the contents of the current directory.
mkdir   | `mkdir new` | Makes a directory.
cd      | `cd new`    | Enters a different directory.
pwd     | `pwd`       | Tells you what directory you are in.

When you first open the terminal you will see a command prompt. You will be in your home directory. If you type pwd, you will see the "path" to your home directory.

The path given to you by pwd is called an "absolute path." If you type an absolute path anywhere in the system, it will always refer to the same place. Absolute paths begin with "/".

A relative path is any path that does not begin with "/". Relative paths are stated relative to your present working directory. If you type "cd ex01" from your home directory, it will go to the directory "ex01" inside your home directory.

Here are a few shortcuts that you can use when forming paths.

 Command | Meaning                    | Detail
 ------- | -------------------------- | ------
 ~       | Home directory.            | A space set aside for each user to store their files.
 .       | The current directory.     |
 ..      | The parent directory.      |
 /       | The root directory.        | The very top of the computer's filesystem.
 pwd     | Present working directory. | Tells you what directory you are in.

Here's a quick exercise to try this all out.

```
mkdir linux_exercise
ls
cd linux_exercise
ls ..
cd ..
ls
mkdir linux_exercise/subdirectory
cd ~/linux_exercise/subdirectory
pwd
cd ~
```

The above is essentially a command-based version of what you're used to doing by double clicking on folders. The command line is capable of a great deal more---in fact, you will be using it to compile your tutorial program! But more on that later. First, you'll need to write some code.

### Tab Completion

Note that the command line has tab-completion. If you start typing the name of a unique file, directory, or command and hit tab, it will finish the name for you. If there is more than one match, all possible options are displayed.

## Text Editor

For the C++ tutorials that we will start with, we will use a text editor called Sublime.

To open Sublime you can do one of two things:

* Open up a terminal window, type in "sublime_text &" and hit Enter. The & tells the computer to allow you to continue to use that terminal while the editor is running.

* Open the lens as before, type in sublime_text and hit Enter. You do not need the & in the lens.

Using sublime and the command line, you will be able to write and execute your tutorial programs.

## Arduino IDE

The robot uses an Arduino microcontroller, so for times when we program the robot, we will want to use the Arduino IDE (Integrated Development Environment).

Opening arduino is the same as opening Sublime, except that you will type "arduino" in either the terminal or the lens.

## Logging Out

Before you leave the lab, make sure you save all your work and log out of the computer, so that it's free for the next person to use it. Open up the account menu in the top right-hand corner of your screen, and click to log out.

Also, please do not reboot the computer. If you are experiencing technical difficulties, resist the urge to try turning the machine off and on again, and instead notify one of the camp staff.

## Next Step

Proceed to ["Welcome!"](/welcome.html)
