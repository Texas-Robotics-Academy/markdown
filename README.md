Archive of old exercises can be found at https://github.com/Texas-Robotics-Academy/markdown/

# List of Lecture Content
## Soldering
* Solder tutorial from Bot'n Roll
* Do a solder joint on webcam in front of class
* Walk through robot assembly steps
## Basic operation of Linux
* The lens
* Sidebar, favorites, alt-tab
* Google Chrome, accessing the Texas Robotics Academy Website
* The terminal - terminator
* cd, ls, mkdir
* arduino
* vscode
* ctrl-z; bg
## Git clone
### 1
* Just demonstrate
## Programming
### Exercise 2 - C++
* int main
* include files
* g++
* make
* cout
### Exercise 2 - Arduino & Bot'n Roll
* setup(), loop()
* Objects - We'll come back to this later, BUT (.notation)
* Boilerplate - Serial.begin(), one.spiConnect, one.stop, one.obstacleSensorsEmitters()
  * Briefly explain what they do
* Serial.print, Serial.println
### Exercise 3 - C++
* cin
* int, float, long, double, bool, string
* =
* \+ \- \* / % ++ --
### Exercise 3 - Arduino & Bot'n Roll
* delay
* one.setLed()
### Exercise 4 - C++
* if, then, else
* == != > < && || !
* for, while, do
### Exercise 4 - Arduino & Bot'n Roll
* Quick discussion of "loop()"
* Global variables
* String, and String(int)
### Exercise 5 - Arduino & Bot'n Roll
* Range sensors
* one.readLeftRangeSensor(), one.readRightRangeSensor() - Range 0-25
### Exercise 6 - C++
* Switch
### Exercise 6 - Arduino & Bot'n Roll
* one.readObstacleSensors()
* one.readButton()
### Exercise 7 - C++
* Functions, classes, and objects, public, private
### Exercise 7 - Arduino & Bot'n Roll
* one.move()
### Exercise 8 - Arduino & Bot'n Roll
* Turn & Push
### Exercise 9 - C++
* Arrays
* char * as a string
* Type casting
### Exercise 9 - Arduino & Bot'n Roll
* Using the Line Sensor
* Values demo
* Thresholding demo
* Max value demo
### Exercise 10 - Arduino & Bot'n Roll
* What is PID Control?
* The setpoint
* Error
* Computing P
* Computing I
* Computing D


# Exercises
## Exercise 1
* Git clone the tutorials
* cd into directory, open vscode
* Background the process, or go to another terminal
* open arduino

## Exercise 2
### C++
* 2.1 Modify the cout statement to print "Welcome to the Texas Robotics Academy!"
### Arduino & Bot'n Roll
* 2.2 Use the one.lcd1 and lcd2 commands to print "Hook 'em", "Horns!"
* 2.3 Use Serial.println() to print on the serial monitor. Watch the output

## Exercise 3
### C++
* 3.1 Area of a rectangle
### Arduino & Bot'n Roll
* 3.2 Print on the LCD "Texas Robotics", "Academy." delay(1000). "Hook 'em", "Horns." delay(1000)
* 3.3 Turn on and off the LED on the robot

## Exercise 4
### C++
* 4.1 Write a for loop. If x \< 10 print something, == print something, > print something
### Arduino & Bot'n Roll
* 4.2 Make a global variable "counter," set it to zero. Inside the loop, use String and String() to make a string that says, "Counter: " next to the value of counter. Print it on LCD 1.

## Exercise 5
### Arduino & Bot'n Roll
* 5.1 Use one.readLeftRangeSensor() and one.readRightRangeSensor(). Print the value on LCD1 and LCD2.

## Exercise 6
### C++
* 6.1 Write a switch. Use cin to take in a value. If the value is 0, print "Zero." If it is 1, print "One." If it is 3, print "three." If it is something else, print "Other".
### Arduino & Bot'n Roll
* 6.2 Use one.readObstacleSensors(). Use a switch. Print whether the neither obstacle sensor, the left, the right, or both are detecting obstacles on lcd1. In the same program. Use one.readButton(). Use a switch. Print whether no button is being pressed, or button 1, 2, or 3 is being pressed on lcd1.

## Exercise 7
### Arduino & Bot'n Roll
* 7.1 Write a class to control the robot's motors. Your class should have 4 variables: lastButton, whichMotor, leftSpeed, and rightSpeed. Your class should have a constructor to initialize the variables. Your class should have 3 methods, other than the constructor: void buttonPress(byte button), void runMotors(), void printMenu(). buttonPress should react to button presses. I used a switch. If button 1 is pressed, it should flip between the left and right motors. Note that holding button 1 would cause the motors to flip continually - way too fast for you to control! So, you should check if button 1 was the LAST button pressed (which means that when you first click button 1, it is pressed, but once you're holding it, you no longer react to it). So, you should only flip motors when button 1 is first pressed. Button 2 and 3 you should be able to hold down. Button 2 should increment leftSpeed or rightSpeed by 1; speeding up the motor, depending on whether the left or right motor are selected. Button 3 should do the same thing, but decrement. If either leftMotor or rightMotor is > 100, set it to 100. If either is less than < -100, set it to -100. Go out to the bridge and make your robot drive in a straight line, and then turn in a circle. Make sure to show a PA your group doing this, controlled by your menu.

## Exercise 8
### Arduino & Bot'n Roll
* 8.1 Turn & Push

## Exercise 9
### C++
* 9.1 Create an array with 10 elements. Use a for loop to fill it with 10 numbers. Use another for loop to print out all of the numbers in the array.
### Arduino & Bot'n Roll
* 9.2 Write a class to do this. Read the values from the Line Follower into an array. There are 8 sensors on the line follower.Use Serial.print to print all 8 values, and then Serial.println to make a new line. Hold the line follower over the line target, connect the robot to the serial port, and watch the output on your Serial monitor.
* 9.3 Copy your 9_2 into 9_3. Make a character array that is 17 elements long. Make a variable called threshold. Make button 2 and 3 adjust threshold up and down, and print it on LCD 1. Make a for loop. Iterate through your array. For the first element of your line follower array, put two ** in the character array if the value is > threshold, and two -- otherwise. Print the output on LCD2. Hold the robot over the line target. You should see ** under the line target where the line is under the robot, and -- everywhere else when your threshold has been correctly adjusted.
* 9.4 Copy your 9_3 into 9_4. Modify findLine. Remove threshold. Use a for loop to find the index of the highest value in your array of line follower values. Render --s everywhere other than that index. Put ** at that index.
* 9.5 Take the highest array value. Scale it so it ranges from -1 to 1.. This is to say, how can you compute so that when it is 0, it's -1, and when it is 7, it's 1? Display your number on LCD1 and validate that it works properly. This will be crucial.




# List of Resources
* Linux Cheat Sheet - Link to Markdown page + PDF & Lecture Slides
* C++ Cheat Sheet - Link to Markdown page + PDF & Lecture Slides

PA's, I need you to write some of these exercises for me. 

# Program Overview
## Day 1
### Lecture 1
* Welcome to Camp
* Soldering Tutorial
### Robot Assembly @ Texas Invention Works
* Soldering exercise
* Robot assembly

## Day 2
### Lecture 2
* Welcome to the Lab
* Using Linux - Make a "Cheat Sheet" for this page
* Introduction to git
* Introduction to C++ Programming
* Introduction to Arduino Programming
