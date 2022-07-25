# Robot Functions
## Documentation 
Feel free to come back to this page to check up on what these functions do.

## `LEDs`

{{ site.data.alerts.callout_code_div }}
```
void ledLeft(boolean state)
void ledRight(boolean state)
```
{{ site.data.alerts.end }}

These functions turn on and off the left and right LEDs respectively, based on whether it is passed `true` or `false`. 

## `lcd#`

You already saw the `lcd#` function in the "Hello World" exercise on the robot. One other important feature of this function we should mention is that it can take any number of arguments - for example,

```cpp
bot.lcd1("Bob is ", 10, " years old!");
```

will print out "Bob is 10 years old!"


## Obstacle Sensors

{{ site.data.alerts.callout_code_div }}
```
double leftObstacleSensor()
double rightObstacleSensor()
```
{{ site.data.alerts.end }}


These functions will return the distance (in meters) from the left or right obstacle sensor to the nearest obstacle. Each sensor is on the front of the robot, pointing out 45 degrees. The range for these values is [0.0,10.0]

All of these functions are accessed in the same way as we accessed the lcd function. In order to call these functions you must attach them to your TexBot object, "bot", with a period.

## Thresholding

In order for the obstacle sensors to be of any meaningful use, we will need to use thresholding. If we want a function of the robot to be triggered based on how close the robot is to an obstacle, we need to check if the returned value from the obstacle sensor functions is greater or smaller than a certain value. That value is your **threshold**. 

In the next two exercises you will need to come up with a good threshold with which to compare the distance between your robot and a wall to trigger changes in the lcd screens and leds.

### Exercise 4.2.1

- Navigate to and open the ex_4_2_1.cpp file located in the src folder of the 4_2 package. It should already be filled with the "empty program" from "Robot Programming Introduction"
- Write a short program that will print "Left Sensor Activated" when the left sensor is activated, "Right Sensor Activated" when the right sensor is activated, and "Both Sensors Activated" when both sensors are activated on the LCD on the robot.
- To test the program:
  - **roslaunch** the box.world launch file
  - **rosrun** your code
  - In order to move the robot closer to a wall, you will have to teleop the robot. `rosrun texas_robotics_academy teleop_texbot`

{{+}}Tutorial 4.2.1, 4_2_1{{+}}


### Exercise 4.2.2

- Instead of just printing which sensor is activated, turn on the corresponding LED to indicate which obstacle sensor has been triggered.

{{site.data.alerts.note}}
Many of you may have issues with this exercise, so please call a counselor!
{{site.data.alerts.end}}

{{+}}Tutorial 4.2.2, 4_2_2{{+}}


{{-}}Exploring the Robot's Motion, virtual/robot_move.md, Next{{-}}

