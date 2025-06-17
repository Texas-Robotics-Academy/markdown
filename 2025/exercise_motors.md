# Exercise 7: Controlling the Motors

Open the ex7.ino file.

I have provided you with the outline of a class called MotorMenu. You are to fill in the details.

{{ site.data.alerts.note }}
This exercise is a bit more complicated than the ones that come before it, but, you get to learn how to steer your robot!
{{ site.data.alerts.end }}

- Note your four class attributes: lastButton_, whichMotor_, leftSpeed_, rightSpeed_

## menu.buttonPress()
- Your class should pass the value from one.readButton() into menu.buttonPress();
- The variable lastButton_ should always store the value of the LAST button pressed.
  - To accomplish this, store the value from the parameter "button" in buttonPress at the end of that class method.
- whichMotor_ is a bool. When it is true, your program should be able to change the value of the right motor. When it is false, your program should be able to change the value of the left motor.
- Use a switch statement in buttonPress.
- If the value is 1 it should
  - Check if lastButton_ is NOT 1.
  - If lastButton_ is NOT 1, it should flip between controlling the left and right motor.
  - As in making whichMotor_ false or true.
- If the value is 2, it should
  - Increment (++) leftSpeed_ if whichMotor_ is false, and increment rightSpeed_ if whichMotor_ is true.
- If the value is 3, it should
  - Decrement -- leftSpeed_ if whichMotor_ is false, and decrement rightSpeed_ if whichMotor_ is true.

The maximum speed that a motor can turn is 100. It can also spin backwards, and a maximum speed of -100.

- Add if statements inside menu.buttonPress(), such that:
  - If leftSpeed_ or rightSpeed_ is greater than 100, it is set to 100.
  - If leftSpeed_ or rightSpeed_ is less than -100, it is set to -100.

## menu.printMenu()

- Make this class method print your menu on LCD 1 and LCD 2
- If the left motor is selected, print a "<--" on LCD 1.
- If the right motor is selected, print a "-->" on LCD 1.
- On LCD 2, print the speed of the left motor + " " + the speed of the right motor.

## menu.runMotors()

- This class method should only be 1 line long, but it should use one.move to spin the motors using leftSpeed_ and rightSpeed_.

## Learning to steer your robot

- Go out onto the bridge.
  - Use your menu to make the robot go forward and backward.
  - Use it to make your robot spin in place.
  - Use it to make your robot turn in a small circle.
  - Use it to make your robot turn in a large circle.


{{+}}Exercise 7, 7{{+}}