# Exercise 10: PID Control

## Exercise 10.1: Controller Interface

- Save ex9_4 as ex10_1.

Write a class called PIDController
- Give it two methods
  - void buttonPress(byte button)
  - void printScreen()
- Give it some variables
  - floats for _kC, _kP, _kI, _kD.
  - An int for which gain is currently being tuned - Similar to _whichMotor and _whichItem in previous menus.
- Write a menu interface, using buttonPress() and printScreen()
  - Make it so you can adjust _kC, _kP, _kI, and _kD

You can pick the ranges that should be the maxima and minima for these variables.
You will want one more variable:
- _increment

Increment will be how much you will adjust your gains up and down when a button is pressed. In previous exercises, you could simply increment by 1 for each button press. That's WAYYY too much for this exercise. Try something like 0.1.

In loop()
- comment out or delete lineFollowerInterface.printScreen()

Make sure your menu can change all of the gains.

{{+}}Exercise 10.1, 10_1{{+}}

## Exercise 10.2: Proportional Control

- Save ex10_1 as ex10_2.

Add a method to PIDController:
- void runMotors(float error)

Add a method to LineFollowerInterface:
- float getPotential()
  - This method should return _linePotential.

In your loop()
- Call PIDController.runMotors()
  - Pass the value from getPotential to runMotors.

In runMotors()
- Compute float leftSpeed and rightSpeed.
  - leftSpeed = _kC + (_kP * error)
  - rightSpeed = _kC - (_kP * error)

{{+}}Exercise 10.2, 10_2{{+}}

## Exercise 10.3: Proportional & Derivative (PD) Control

- Save ex10_2 as ex10_3.

Add a variable to PIDController:
- float _lastError = 0;
  - This will store the error from the previous step.
  - At the end of runMotors() you should store error in _lastError.

Edit runMotors()
- At the start of the method, compute float d - your gradient (derivative)
  - d should be error - _lastTerror

In runMotors()
- Compute float leftSpeed and rightSpeed, using an updated formula for your PD controller
  - leftSpeed = _kC + (_kP * error + _kD * d)
  - rightSpeed = _kC - (_kP * error + _kD * d)

{{+}}Exercise 10.3, 10_3{{+}}

## Exercise 10.4: Proportional, Integral, & Derivative (PID) Control

- Save ex10_3 as ex10_4.

Add a variable to PIDController:
- float _i = 0;
  - This will store the Reimann Sum (integral) of error.

Edit runMotors()
- At the start of runMotors() you should add error to _i
- I is cumulative for the entire run of the robot. You set it to 0 when the robot starts running, and just keep adding to it.

In runMotors()
- Compute float leftSpeed and rightSpeed, using an updated formula for your PD controller
  - leftSpeed = _kC + (_kP * error + _kD * d + _kI * _i)
  - rightSpeed = _kC - (_kP * error + _kD * d + _kI * _i)

{{+}}Exercise 10.4, 10_4{{+}}

{{-}}RACE!, 2025/exercise_race.md, Next{{-}}