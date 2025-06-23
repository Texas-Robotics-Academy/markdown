# Exercise 2: Hello World!

{{ site.data.alerts.note }}
Go ahead and do all of the parts of Exercise 2 (2.1, 2.2, and so forth). Make sure to have the Program Assistants check at the end.
{{ site.data.alerts.end }}

Hello World is a classical computer program, designed to familiarize programmers with the basic syntax of a language and build systems.

Look at ex2/ex2_1.cpp in Visual Studio Code.


{{ site.data.alerts.terminal_commands }}
cd ex2
make
./ex2_1
{{ site.data.alerts.terminal_commands_end }}

Hello World should print on the screen.


## Exercise 2.1:

- Modify the Hello World program so that it prints, "Texas Robotics Academy!"
- Next, add a second line of text that says, "Hello World in C++!"

{{+}}Exercise 2.1, 2_1{{+}}


{{ site.data.alerts.note }}
Before you compile Bot'n Roll code, you have to install the Bot'n Roll Library in Arduino.

Instructions can be found on page 24 of the slides, found [Here](https://drive.google.com/file/d/1xN-hKcO_3fxsRq1eVrVbWX-4r4rsxufk/view?usp=drive_link)
{{ site.data.alerts.end }}

## Exercise 2.2:

Go to your Arduino IDE. Navigate to the ex2_2.ino file (in ex2/ex2_2).

- In your loop() use one.lcd1() to print "Hook 'em" and one.lcd2() to print "Horns!"

{{+}}Exercise 2.2, 2_2{{+}}


## Exercise 2.3:

Go to your Arduino IDE. Use the File/Save As menu item to save ex2_2 as ex2_3, so that your directory structure looks like

ex2  
ex2/ex2_2  
ex2/ex2_3

- Use Serial.println() to print "Texas Robotics Academy" to the serial port. Open the Serial Monitor in the Arduino IDE to see your output.

{{+}}Exercise 2.3, 2_3{{+}}

{{-}}Exercise 3: Variables and a few robot functions, 2025/exercise_variables_delay.md, Next{{-}}