# Exercise 8: Turn & Push

## Exercise 8.1: Reading the Obstacle Sensors
In Exercise 5.1, you read the range sensors on the robot. Now, we will use them to control the robot.

- Make a directory called ex8.
- Save ex7_1 as ex8_1.
- Comment out menu.buttonPress(), menu.runMotor(), and menu.PrintMenu() from loop()
  - Basically all of the code in loop() - yes - but you'll need it later.
- In setup() use one.obstacleSensorsEmitters(const bool state) to turn on the obstacle sensors
- Write a class. Call it TurnAndPush. Declare it AFTER MotorMenu and AFTER "MotorMenu menu".
- Give TurnAndPush a class method. Call it void reactToObstacles().
- Inside void reactToObstacles():
  - Make a variable called obstacleDetection.
  - Make a variable called threshold.
  - Use one.readLeftRangeSensor(), one.readRightRangeSensor(). Store the values of both in variables, leftO and rightO. (Calling them again can change the value they return.)
  - If neither is > threshold, make obstacleDetection = 0.
  - If only left is > threshold, make obstacleDetection = 1.
  - If only right is > threshold, make obstacleDetection = 2.
  - If both are > threshold, make obstacleDetection 3.
- Make reactToObstacles() print on LCD 1:
  - "No obstacle" - When there is no obstacle.
  - "Left" - When there is an obstactle on the left side.
  - "Right" - When there is an obstacle on the right side.
  - "Both" - When both obstacle sensors have been activated.

{{+}}Exercise 8.1, 8_1{{+}}
  
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

- Comment out the part of reactToObstacles() that prints to LCD 1, or simply delete it.

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

{{-}}Exercise 9: The Line Sensor, 2025/exercise_line_sensor.md, Next{{-}}