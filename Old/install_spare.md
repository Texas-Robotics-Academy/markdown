
Let's look at this code line-by-line.

```cpp
#include <iostream>
``` 

This line **includes** `iostream` into our program, making its contents available to our program. `iostream` is what is called a **header** or a **header file**. It contains the code needed to interface a library called the *Standard Input/Output Streams Library*. Including `iostream` allows us to use `cout`.

In general you will enclose header names in angle brackets. When you write your own headers, you will probably enclose them in double quotes. 

```cpp
using namespace std;
```

This line tells the compiler that if things are included in the *std* namespace, they don't need to lead the name with *std*. In the program here, *cout* is a part of the *std* namespace. If we did not **use** the *std* namespace, we would write it as `std::cout`.

{{ site.data.alerts.tip }}
For the purposes of this camp, just include *using namespace std* in your programs. Namespacing will become important if you continue programming, but we only use one namespace in this camp.
{{ site.data.alerts.end }}

```cpp
int main(){
```

This next line defines the *main* function. This tells the computer that there is a function called *main* that **returns** an integer (more on this later).

The code for *main*, like the code for all functions, is wrapped in curly braces. We call the code wrapped in braces a **block**. In this line, we are beginning the block with an opening brace.

```cpp
cout << "Hello World!" << endl;
```

We only have one command for this program. Here we tell the computer to use *cout* and then put what we want to print after *<<*.

The double left-angle brackets are like an arrow pointing toward *cout*, sending something into it (in this case, *"Hello World"*) to *cout*.

After *"Hello World"* there is `<< endl`, which tells the program to end the line of text and follows it with a **newline**, which literally tells the terminal to go to a new line. This is kind of like hitting *enter* at the end of a line when you're typing text.

We put quotation marks around the words we want to display (this is called a **string**). In cpp, every line of code (ones without braces) ends in a semi-colon.

So, you are telling the computer to send *"Hello World!"* as a string to *cout* to be displayed on the screen.

```cpp
return 0;
```

This last line **returns** the number zero. We will get into what this means in a later tutorial, but for now, we can understand it as telling the computer that our program ran properly.

We then use a closing brace to end the function, and with it, the program.

## Compiling and Executing from the Command Line

Compiling code is the act of turning your code into a program that the machine can **execute** or run.

To compile your code, we will use the GNU C++ compiler, better known as *g++*.

- Go back to your terminal where you should be in ~/cpp_exercises/3_1
  - Use the `cd` command to get there if you aren't there already!

{{ site.data.alerts.terminal_commands }}
g++ ex_3_1.cpp -o HelloWorld
{{ site.data.alerts.terminal_commands_end }}

What does this line do?

*g++* runs the g++ compiler.

*ex_3_1.cpp* is the file to be compiled. In this case, it is the file that we just wrote. In future usages of g++, replace *ex_3_1.cpp* with the file that you intend to compile.

*-o HelloWorld* tells the compiler that the compiled program should be named *HelloWorld*. If you typed *-o MyProgram*, it would name your program *MyProgram*.

Hopefully, your program just compiled.

- Check the output in the terminal to see if the build was a success.
  - If your build is successful, there will be no output.
- Run your program

{{ site.data.alerts.terminal_commands }}
./HelloWorld
{{ site.data.alerts.terminal_commands_end }}


{{ site.data.alerts.note }}
Remember, this is a relative path, so this literally tells the computer, "Run the HelloWorld that is in this directory."
{{ site.data.alerts.end }}

{{ site.data.alerts.callout_synchronize }}
Many of you will have problems right now, so, we'll synchronize to get everyone through their errors.
{{ site.data.alerts.end }}

If you ever forget how to compile a C++ program, we've provided an example in the [documentation](docs.html) that you can always reference in the future.

### Exercise 3.1:

- Modify the Hello World program so that it prints, "Hello <Your Name>!"
    - For example, if your name is Justine, it would display, *Hello Justine!*
- Next, add a second line of text that says, "Programming is actually pretty fun when you get right down to it."

{{site.data.alerts.tip}}
From here on out you will be creating new files for each exercise you do. It would be a good idea to name the files for each exercise according to the exercise name. For example, directory 3_1 will contain exercise ex_3_1.cpp, and directory 3_2 will contain exercises ex_3_2_1.cpp, ex_3_2_2.cpp, and ex_3_2_3.cpp
{{site.data.alerts.end}}

{{+}}Tutorial 3.1, 3_1{{+}}

## Next Step

Proceed to ["Simple Math and User Input"](simple_math_user_input.html).









# Installation

Since you will be working from home, we will need a way for you to run these tools on your home machine. There are three options here.

* Native Ubuntu 18.04 Installation - We recommend this only for people who already have Linux installed on their machines. We only support Ubuntu 18.04 for the Texas RoboCamp, as this is the target platform of ROS Melodic. If you are running a different version of Ubuntu, please run 18.04 either from a virtual machine or from the thumb drive.

* Live Thumb Drive - We distributed 64 GB USB 3.0 thumb drives to all of you. Running from a thumb drive involves downloading an image from the internet and writing it to the drive. You then boot your machine from the thumb drive every time you want to us Linux.

* Virtual Machine - We also provide instructions for how to run a virtual machine on your computer. A virtual machine provides a way to run a "guest" operating system inside your computer's OS, which will allow you to run Linux on a Windows machine or a Mac with no problems.

Next steps:

* If you want to run from a Live Thumb Drive, proceed to the next section ("Running from a Live Thumb Drive").

* If you want to run from a Virtual Machine, skip to "Installing with a Virtual Machine"

* If you want to run from a Native Ubuntu 18.04 Installation, skip to "Setting up the Robocamp Software"




## Installing with a Virtual Machine

### What is a Virtual Machine?

A Virtual Machine (VM) is like a computer inside of your computer. It is an environment that runs like a normal program on your machine, but it emulates a fully-functional system, just like if you bought another computer! It has its own virtual hard drive, memory, CPU, and devices that it creates using resources from your computer. 

We will be creating a virtual machine that we can use to run and develop software from during the course of the camp.

### Preconfiguration (for Windows)
Before we get started, if you have a Windows machine, you will have to first allow your computer to use its resources to create a virtual machine by enabling virtualization.

1. Restart your computer.

2. On a keyboard, repeatedly press F2 (or F10 for some machines) as your system is starting up, before the Windows logo appears. Note that wireless keyboards may not work for this.

3. Go to the Configuration/Advanced Settings page.

4. Find the Virtualization/Virtual/SVM option (the name may be different) and turn it on.

5. Save the changes and restart.


{{ site.data.alerts.img_75 }}
images/bios.png
{{ site.data.alerts.img_75_end }}

{{ site.data.alerts.note }}
The officially supported virtual machine software for this camp is **VirtualBox**. If you would prefer to use **VMWare** (an alternate software) instead, there are installation instructions for trial versions after this section. Both will work for the purposes of this camp.
{{ site.data.alerts.end }}


### **Installing VirtualBox**
### Downloading
**Windows:**
1. Go to https://www.virtualbox.org/wiki/Downloads.

2. Under the section for the latest version (6.1.10 at the time of writing), click the download link for “Windows hosts”.

3. Open the installer.

4. Follow the instructions to install VirtualBox.

**Mac:**
1. Go to https://www.virtualbox.org/wiki/Downloads.

2. Under the section for the latest version (6.1.10 at the time of writing), click the download link for “OS X hosts”.

3. Open the installer and double-click the “VirtualBox.pkg” file.

4. Follow the instructions to install VirtualBox.

{{ site.data.alerts.important }}
The first time you install VirtualBox, you may see a pop-up saying something along the lines of “System software from Oracle America was blocked”. If you see this message:
* Open System Preferences.

* Select the Security and Privacy menu.

* Click “Allow”.

{{ site.data.alerts.end }}

### Creating the virtual machine
1. Start downloading the installer for Ubuntu 18.04.4 from https://releases.ubuntu.com/18.04.4/ubuntu-18.04.4-desktop-amd64.iso (this is a large file, and will take some time to download).

2. Open VirtualBox.

3. Click the “New” button to create a virtual machine.

4. In the window that appears:
    * Specify “Texas Robocamp 2020” for the name.

    * Leave the “Machine Folder” as-is.

    * Set the type to “Linux” and the version to “Ubuntu (**64-bit**)”. (Note that VirtualBox tries to predict these settings based on the name - you will need to correct them after you enter the name.)

    * Click Continue.

5. Set the slider for the amount of memory to half the maximum value (which should be the amount of RAM on your system) and click Continue.
    * If you have 32 Gigabytes / 32768 MB of RAM, this will be 16384 megabytes.

    * If you have 16 Gigabytes / 16384 MB of RAM, this will be 8192 megabytes.

    * If you have 8 Gigabytes / 8192 MB of RAM, this will be 4096 megabytes.

6. Select “Create a virtual hard disk now” and click Create.

7. Select “VDI” and click Continue.

8. Select “Fixed-size” and click Continue.

9. Set the size to 15 GB and click Create (leave the file name and location as-is).

10. Click the Settings button.

11. Under the System tab, go to the Processor section. Set the number of cores as high as the green line reaches. Leave the other settings alone.

12. Under the Display tab, go to the Display section. Set the Video Memory setting as high as possible. Leave the other settings alone.

13. Click OK.

Once you are done, your screen should look something like this.

{{ site.data.alerts.img_75 }}
images/virtualboxmenu.png
{{ site.data.alerts.img_75_end }}

### Installing Ubuntu
1. Select the “Texas Robocamp 2020” virtual machine and click Start.

2. Click the folder icon. Click “Add” and select the Ubuntu ISO file you downloaded earlier.

3. Click Choose, then click Start.

4. Once you get to the screen that says “Try Ubuntu”/”Install Ubuntu”, click the Install button.

5. If you use a custom keyboard layout, select the layout you use. Otherwise, click Continue.

6. Select “Minimal installation”, “Download updates while installing”, and “Install third-party software for graphics”. Then click Continue.

7. Select “Erase disk and install Ubuntu”. Click “Install Now”. On the pop-up, select “Continue”.
    {{ site.data.alerts.note }}
    Don’t worry about the warning - this won’t affect the rest of your computer. The installer only has access to the virtual machine you created in VirtualBox.
    {{ site.data.alerts.end }}

8. Select your local time zone on the map and click Continue.

9. Fill in your name. Set the username to “robocamp” and the password to “robocamp2020” (without the quotes). Select “Log in automatically” and click Continue.

10. Once the install finishes, click Restart.

11. When the screen says “Remove the installation medium”, check that the circular CD icon in the bottom bar of the VirtualBox window is gray. If not, click it and click Remove. Once the icon is gray, press Enter.

12. On the main screen, click Next on each screen until you get to the “You’re ready to go!” screen. Click Done.

13. If you see a pop-up saying “Updated software has been released”, close the window - they will be automatically installed as part of the setup process.

Your screen should look something like this when your installation is complete.

{{ site.data.alerts.img_75 }}
images/ubuntudesktop.png
{{ site.data.alerts.img_75_end }}

### Installing the Guest Additions
1. Go to the VirtualBox menu bar. Under the “Devices” menu, click “Insert Guest Additions CD image”.

2. If you don’t see the menu, make sure you are still in the virtual machine window.
    {{ site.data.alerts.note }}
    The first time you do this, you will see a series of prompts to download it. Just click OK at each step.
    {{ site.data.alerts.end }}

3. A popup will appear in Ubuntu. Click Run and enter your password.

4. Once the “Press Return to close this window” message appears, press Enter.

5. Restart the virtual machine by clicking the arrow in the top-right corner and clicking the Power button. Select Restart in the popup.
    {{ site.data.alerts.tip }}
    Whenever you are done using VirtualBox, you should turn off the virtual machine through this menu. Instead of clicking Restart, you will click Power Off.
    {{ site.data.alerts.end }}

{{ site.data.alerts.important }}
Congrats! You have now successfully set up your VirtualBox system. Now move to the bottom of this page to install the Robocamp software.
{{ site.data.alerts.end }}





