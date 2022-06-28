# Getting to a Terminal

1. Click on the 3x3 formation of dots in the lower left-hand corner.
2. Type in "terminal."
3. A terminal window will open.

# Changing Windows

* Hit alt-tab to cycle windows, or click on the icons on the launcher.

{{ site.data.alerts.note }}
This basically the same as on Mac or Windows.
{{ site.data.alerts.end }}

# Locking Frequently-Used Programs to the Launcher

1. Right-click on the application that you would like to lock to the launcher.
2. Click "Add to Favorites."

{{ site.data.alerts.note }}
If this doesn't make sense to you, skip it.
{{ site.data.alerts.end }}


# Basic Linux Commands

Command | Example | What it does
------- | ------- | ------------
ls | `ls .` | Lists the contents of the current directory.
mkdir | `mkdir new` | Makes a directory.
cd | `cd new` | Enters a different directory.
pwd | `pwd` | Tells you what directory you are in. "Present Working Directory"

When you first open a terminal you see a command prompt and you will be in your home directory.

If you type pwd, you will see the "path" to your home directory.

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

{{ site.data.alerts.terminal_commands }}
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
{{ site.data.alerts.terminal_commands_end }}

{{ site.data.alerts.tip }}
**Tab Completion**

The command line has tab-completion. If you start typing the name of a file, directory, or command and hit tab, it will finish the name for you. If there is more than one match, all possible options are displayed.
{{ site.data.alerts.end }}

# Text Editor

For the C++ tutorials, we will use an IDE (Integrated Development Environment) called Visual Studio Code.
To open VSCode you can do one of two things:

* Open a terminal. Go to the directory containing the code you want to edit. Type "code . &", hit Enter. 
* Open the lens (the dots) as before, type in code, hit Enter.

# Arduino IDE

The robot uses an Arduino microcontroller (like a small computer). For programming the robot, we will use the Arduino IDE.

Opening arduino is the same as opening VS Code, except that you will type "arduino" in either the terminal or the lens.

# Logging Out

Before you leave the lab, make sure you save all your work and log out of the computer so that it's free for the next person to use it. Open the account menu in the top right-hand corner of your screen and click log out.

{{ site.data.alerts.warning }}
Do not reboot the computer. If you are experiencing technical difficulties, notify one of the camp staff.
{{ site.data.alerts.end }}

{{-}}Introduction to C++ Programming, in_person/programming_intro.md, Next{{-}}