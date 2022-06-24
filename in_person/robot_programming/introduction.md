## Getting Started
Now that you've learned the basics of C++, we can move on to programming on the robot!

- Open up the Arduino IDE.

### A Boilerplate Bot'n Roll Program

Here's a simple, brief program that you can copy as a sort of "empty" program to start your projects with.

```
#include <BnrOneA.h>
#include <EEPROM.h>
#include <SPI.h>
BnrOneA one;

#define SSPIN 2

void setup() {
  // put your setup code here, to run once:
  Serial.begin(57600);
  one.spiConnect(SSPIN);
  one.stop();
}

void loop() {
  Serial.print("Hello World!");
}
```

#### A Concept You Haven't Seen Before: Global Variables

A <b>global variable</b> is a variable whose scope is the entire program.

Well, that's a half-truth. It's the entire file that you are editing (and there are ways to make it accessible throughout the program, as well, if you have multiple files).

Remember in the C++ tutorial where variables were scoped to functions?

We told you that you should declare all of your variables at the start of your function, and that they are scoped to the function.

If I hava a function `a` with variables in it, and a function `b` with variables in it, `a` couldn't access the variables of `b`, and vice-versa.

If you declare a variable outside any of the functions in your program, as is done with `BnrOneA one`, you can access if throughout the program.

Why would you want to do this?

Well, in this program, the global variable `one` is accessed in `setup`, but can also be accessed in `loop`.

The variable `Serial` is also global, but it is declared in the Arduino library.

{{ site.data.alerts.tip }}
<ul>
<li>The variable `Serial` is declared in `HardwareSerial.h`, which is included in `Arduino.h`, which is included in `BnrOneA.h`.</li>
<li>The developer who developed `HardwareSerial.h` only concerned themselves with getting the serial port to work. The Arduino developer used the work of the developer who did `HardwareSerial.h` to develop `Arduino.h`. The Bot'n Roll folks used Arduino to build the robot. We're using `BnrOneA.h` to develop our software.</li>
</ul>
{{ site.data.alerts.end }}

#### `Setup`
Arduino programs are C++ programs.

After practicing C++ the first thing that you are likely to notice is the lack of a `main`.

Instead, the code that we will be using is divided into two functions, `setup` and `loop`.

`setup` is always called first. It is sort of like a constructor for setting up the robot. Things in `setup` happen once, when the robot is started.

#### `Loop`
`loop`, on the other hand, is called over and over. You can think of there being a `while` loop running on the robot which runs the `loop` command repeatedly as long as the power switch on the side of the robot is flipped on.

If you connect the Arduino IDE and use the Serial Monitor, you will notice "Connected and Running!" printing repeatedly on the serial monitor. It is sent over the USB port every time the `loop` function is called.


### The Header Files

```
#include <BnrOneA.h>
#include <EEPROM.h>
#include <SPI.h>
```

#### `BnrOneA.h`
`BnrOneA.h` contains code specific to the Bot'n Roll One A robot which we are programming. There is a whole API which has been defined to access the functionality of this robot, and we will go step-by-step through this API 

#### `EEPROM.h`
`EEPROM.h` allows you to interact with the EEPROM on the Atmega328 microcontroller. This is sort of like saving files to a hard drive. Information on the EEPROM persists when the robot is shut off. This could be useful, for instance, if you solved a maze and wanted to store the solution to it, or if you programmed your robot to draw a picture on the floor and wanted to store the picture.

#### `SPI.h`
`SPI.h` provides access to the Serial Peripheral Interface.

### The BnrOneA Class - Your Primary Interface to the Bot'n Roll API

```
BnrOneA one;
```

The `BnrOneA` class is your primary interface to interacting with the robot, through which you will read data from and control the robot.

### The rest of the code

Here, we'll quickly tell you what's going on with the rest of the code.

#### `#define SSPIN 2`

`#define` is what is called a preprocessor directive.

The C++ preprocessor gives instructions to the compiler for how to treat the code.

`#include` is actually also a preprocessor directive. What it says is "copy this whole file right here."

`#define`, as is used here, is used sort of like a variable for the compiler. Anywhere where you see `SSPIN` in the rest of the code, a 2 is actually placed there before compilation.

You won't need to worry about this in order to program your robot. We just didn't want to leave a piece of the code that you saw unexplained.

#### `Serial.begin`

```
Serial.begin(57600);
```

This sets serial up connection and specifies its speed (baud).


{{ site.data.alerts.tip }}
<ul>
<li>When using the Serial Monitor, make sure that the baud setting on the monitor is the same value as the number passed into Serial.begin(), or your output will not be understandable.</li>
<li>Similarly, if you decide to write C++ code which communicates over the USB port, you will need the baud rates to match between the robot and computer sides of the connection, or it will not work properly.</li>
</ul>
{{ site.data.alerts.end }}

#### `one.spiConnect`

```
one.spiConnect(SSPIN);
```

The Bot'n Roll uses SPI to communicate between the two microcontrollers on the robot: the Atmega328 - which we will be programming using Arduino, and the PIC18F45K22 - which we will not directly be programming.

{{ site.data.alerts.tip }}
The BnrOneA class formats messages to the PIC18F45K22, which are communicated using SPI. The PIC18F45K22 then directly handles some of the low-level control of the robot.
{{ site.data.alerts.end }}

This line of code configures the connection between the two microcontrollers so the robot can operate properly.

#### `one.stop`

```
one.stop();
```

This stops the motors on the Bot'n'Roll One. This line of code is just a precaution to ensure that the robot doesn't start moving for no reason.

#### `Serial.print`

```
Serial.print("Hello World!");
```

The `Serial.print` function for the Serial class similarly to `cout` in C++. It allows you to send data across the USB cable back to the computer.

## Hello World - On the Robot's LCD

Now that we're developing software on the actual robot, let's go ahead and write a new "Hello World" program. However, instead of just printing "Hello World" on the computer screen, we're going to print it on the robot's LCD screen! To do this, we'll need to use a new function in the Bot'n'Roll API, `lcd#()`.

### The `lcd` Function

```
void lcd#()
```

This function is actually one of many different `lcd#` functions, and each one takes in different arguments. The Bot'n'Roll has two lines of LCD output. Calling `lcd1` or `lcd2` specifies which line you would like for your text to appear on. There is no concept of a "carriage return," "\n," or `endl` that is useful here.

When calling this functions accept the following combinations of parameters:

- lcd#(string[])
- lcd#(num)
- lcd#(string[],num)
- lcd#(num1, num2)
- lcd#(num1, num2, num3)
- lcd#(num1, num2, num3, num4)

Here are some examples of how you could use these functions:

```
one.lcd1("The number is", 12); // lcd#(string[],num)
one.lcd2(1, 2); // lcd#(num1,num2)
```

### Exercise 4.1.1

- Write your first Hello World program on the robot!

- Create a new Arduino program, go to "File -> New".

- Copy the short program above into your Arduino IDE to set up your program, and save your program in an appropriate place on your computer (along with the other exercises you've done is a good idea). Just like the other exercises, give your program and the folder you work in the same name.

- Make this program say "Hello World!" on the first line in the LCD, and "Texas RoboCamp!" on the second line.

## `delay`
One function that you will find helpful this week is `delay`

```
void delay(milliseconds)
```

This function pauses the program for the amount of time specified in milliseconds.

Basically, you want to use `delay` whenever you want the robot to enter a state for a specified period of time, or when you want to slow down and break down a program so you can see what the robot is doing. Maybe the robot should drive forward for 1 second and then stop, or maybe the robot should simply take a pause after doing something so you can see where one thing stops and another begins. `delay` allows you do do this.

{{ site.data.alerts.tip }}
1000 milliseconds = 1 second
{{ site.data.alerts.end }}


### Exercise 4.1.2

Modify your program to:

- Say: "Hello World!" on the first line in the LCD, and "Texas RoboCamp!" on the second line.
- Wait 2 seconds
- Say: "Hook 'em" on the first line in the LCD, and "Horns!" on the second line.
- Then repeat this in a loop, after waiting 2 seconds with "Hook 'em Horns!" displayed.

{{ site.data.alerts.tip }}
You can modify this exercise to use whatever cheer you like. The point is to learn how the code works.
{{ site.data.alerts.end }}

{% include callout_red_cup.html task="[Exercise 4.1.1, Exercise 4.1.2]" %}

## Next Step

Proceed to ["First Few Functions & Exploring the Obstacle Detector"](/first_few_functions.html)
