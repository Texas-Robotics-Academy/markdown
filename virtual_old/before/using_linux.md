# Introduction to Linux 

Most robotics programming is done using the Linux operating system. This is mainly due to the large amount of open-source robotics software that has been developed on it - in fact, Linux itself is **open-source**. Open-source software is software that is free to use, distribute to others, and modify. This means that you can download the entire source code for Linux online - and even help contribute to it! Linux offers a variety of free easy-to-use tools for software development that will help us along our way in constructing and programming our robots. We will be using the **Ubuntu distribution** of Linux, which is one of many different distributions (versions) of the Linux operating system. Ubuntu is one of the most popular Linux distros, and is the main operating system used here in UTCS.

# Getting to a Web Browser

A grid of nine dots will be displayed on the launcher to the left of the monitor in the bottom left-hand corner.

1. Click on the grid icon. This will open the "applications overview".
2. Type in either "google-chrome" or "firefox" depending on which browser you would like to use. Neither browser is better than the other for this camp. This is purely a matter of personal preference.

3. Go to https://texas-robocamp.com/ to get to this site. Of course, you're already here.


# Getting to a Terminal

1. Click on the applications overview button

2. Type in "terminator."

3. A terminal window will open.

{{site.data.alerts.note}}
The easiest way to access Terminator is to hit Ctrl-Alt-T
{{site.data.alerts.end}}


## Terminator

There are lots of different alternatives to the basic terminal. We will be using Terminator, which is already installed on your machine. Terminator works very similarly to the basic terminal, but has the added feature of being able to have multiple panes open at once in the same window. We will often need multiple terminals open; using terminator makes it easier to keep track of these.

- `ctrl` + `shift` + `o`: Split the current window horizontally

- `ctrl` + `shift` + `e`: Split the current pane vertically

- `ctrl` + `shift` + `w`: Close the current window

# The Super Key

Much like how Windows has the start key and MacOS has the command key, Linux has what we call the `super` key. By default, this will be either your start or command key. Pressing `super` by itself will also open the applications overview.

# Changing Windows

This is similar to operating systems such as Windows and Mac OS. Hit `alt`+`tab` or `super`+`tab` to cycle windows, or click on the icons on the launcher.

# Snapping Windows
The version of Linux we're using lets you easily maximize windows and snap them to half of the screen. To do so, simply press `super`+`arrow-key` 

- `Super`+`Up`: make the window fill the screen 

- `Super`+`Left`: Snap the window to the left half of the screen

- `Super`+`Right`: Snap the window to the right half of the screen

- `Super`+`Down`: Unsnap the window, returning it to its normal size

# Locking Frequently-Used Programs to the Launcher

1. Right-click on the application that you would like to lock to the launcher.

2. Click "Add to Favorites."

# Basic Linux Commands

Here a few commands you will need during the course of this camp. Try them out.

Command | Example | What it does
------- | ------- | ------------
ls | ls . | Lists the contents of the current directory.
mkdir | mkdir new | Makes a directory.
cd | cd new | Enters a different directory.
pwd | pwd | Tells you what directory you are in. "Present Working Directory"

When you first open the terminal you will see a command prompt. You will be in your home directory. If you type `pwd`, you will see the "path" to your home directory.

The path given to you by `pwd` is called an "absolute path." If you type an absolute path anywhere in the system, it will always refer to the same place. Absolute paths begin with "/".

A relative path is any path that does not begin with "/". Relative paths are stated relative to your present working directory. If you type "cd Downloads" from your home directory, it will go to the Downloads directory inside your home directory.

Here are a few shortcuts that you can use when forming paths.

 Shortcut | Meaning | Detail 
 ------- | ------- | ------
 ~     | Home directory.            | A space set aside for each user to store their files. 
 .     | The current directory.     | Where you are now, in the filesystem.                                                      
 ..    | The parent directory.      | The directory in which the current directory is stored.                                                      
 /     | The root directory.        | The very top of the computer's filesystem.            

Here's a quick exercise to try this all out.


{{ site.data.alerts.terminal_commands }}
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
{{ site.data.alerts.terminal_commands_end }}

This is basically a text-based version of double clicking on folders, but the command line is a powerful tool which you will use all week.

# Tab Completion

The command line has tab-completion. If you start typing the name of a file, directory, or command and hit tab, it will finish the name for you. If there is more than one match, all possible options are displayed.

{{site.data.alerts.tip}}
Don't forget about tab completion! It's a HUGE timesaver, especially when you have to type long commands.
{{site.data.alerts.end}}

As an example, make sure you are in your home directory:

{{ site.data.alerts.terminal_commands }}
cd ~
{{ site.data.alerts.terminal_commands_end }}

There should be a Documents directory inside your home directory. You can check this by typing:

{{ site.data.alerts.terminal_commands }}
ls
{{ site.data.alerts.terminal_commands_end }}

Now in your terminal, type "cd Doc" and hit tab. The terminal should have auto-filled the line with "Documents/". When you click enter, you will be led into the "Documents" directory.

# Bash History
By default, all of your previous commands are stored in the order you typed them in ~/.bash_history. This allows for you to easily run previous commands without having to type them over and over, simply by hitting the `up-arrow` on your keyboard while you're in the terminal. Try it right now, and you should see `cd ~` appear on your screen (unless you've typed a new command since we explored the basic commands.)

# VSCode 

We will using an IDE called Visual Studio Code (VSCode) to develop our software during the camp. An **IDE** is an Integrated Development Environment, and they are very useful when writing software due to features like syntax highlighting, code completion, debugging tools, etc.

To open VSCode you can do one of two things:

* Open a terminal, type `code` and hit Enter.

* Open the applications overview and type `vscode` and select the icon for VSCode.


# Shutting Down

Before you finish for the day, make sure you save all your work and turn off the computer. Open the account menu in the top right-hand corner of your screen, click the shut down icon, and select shut down from the power options.

{{site.data.alerts.note}}
If you are running Ubuntu from a USB, please do not unplug the USB before your computer has fully shut down, as this may corrupt files on the USB.
{{site.data.alerts.end}}

# Next Step

Proceed to ["Welcome to Camp!"](/welcome.html)
