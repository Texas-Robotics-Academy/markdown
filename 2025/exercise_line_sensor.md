# Exercise 9: The Line Sensor

{{ site.data.alerts.note }}
Obstacle sensors are neat, but in this exercise, you'll read and threshold the line sensor. The techniques you'll use are basic computer vision techniques.
{{ site.data.alerts.end }}

## Exercise 9.1: Arrays
The line sensor uses an array, so we want you to practice arrays first.

Look in ex_9. There is already an ex9_1.cpp file in there for you to edit.

{{+}}Exercise 9.1, 9_1{{+}}
  
## Exercise 8.2: Updating MotorMenu

- Save ex8_1 as ex8_2.
- Right now, your MotorMenu has:
  - _whichMotor
  - _rightSpeed
  - _leftSpeed

Change it!

- Delete runMotors().

Your robot will now have two modes of operation. One in which it simply drives forward, and one in which it does the "backward turn," where it drives backwards while turning. 

A few notes about turn and push:
- Regardless of what side the sensor sees an obstacle on, the robot should always back up in the same direction.
- It should drive back and turn simultaneously. It shouldn't drive backward and THEN turn.

You'll add a few variables to your menu. Before, your robot had a variable saying which motor was being changed. Now, you'll have four values to change:
- _forwardSpeed - (Ranging from -100 to 100)
- _backLeft - (Ranging from -100 to 100)
- _backRight - (Ranging from -100 to 100)
- _backupTime  - (Should be positive)
- Instead of _whichMotor, you'll have _whichItem

- Modify your buttonPress() and printMenu() methods. buttonPress() should allow you to change _forwardSpeed, _backLeft, _backRight, and _backupTime. printMenu() should print the values of these new variables, rather than the old ones.


{{+}}Exercise 8.2, 8_2{{+}}

## Exercise 8.3: Updating TurnAndPush

You're going to add two functions to MotorMenu:
- forward() - Which should use one.move to drive the robot forward at _forwardSpeed.
- backwardTurn() - Which should use one.move to drive the robot in a backward turn using _backLeft and _backRight. It should use a delay to pause for _backupTime, so the robot backs up for that long.

Now, you will modify TurnAndPush.
- Comment out the one.lcd1 call in reactToObstacles(byte obstacles)
- Make it so that when reactToObstacles receives 0 (no obstacle), it calls motorMenu.forward()
- Make it so that when reactToObstacles receives anything else (it sees an obstacle), it calls motorMenu.backwardTurn()

{{+}}Exercise 8.3, 8_3{{+}}

## Exercise 8.4: The L

Out on the bridge, there is a big "L" made out of wood.

Your robot should start on one side, and do a turn and push so it gets to the other side of the L. Remember, a turn and push is MULTIPLE turns. It shouldn't go, back up once, and turn. That doesn't work in more general cases. It should be like a 3-point turn in a car, where the car goes forward and backs up multiple times.

You will definitely need to tune the variables in the menu that you've created. You may need to tune your obstacle sensors with a screwdriver.


{{ site.data.alerts.good_job }}
Congrats! This is your robot's first autonomous behavior!
{{ site.data.alerts.end }}

{{+}}Exercise 8.4, 8_4{{+}}