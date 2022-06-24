---
title: "Exploring the Robot's Motion"
tags: [robot programming]
keywords:
sidebar: tutorials
permalink: move_the_robot.html
---

In this tutorial, you will create a program that uses the buttons to control the speed of the left and right motors separately. You will then use this program to learn how the robot can perform simple turns, speed up, and apply its brakes.

## The Move Function

```
void move(int speedL,int speedR);

one.move(speedL,speedR);
```

The `move` function is part of the `BnrOneA` class, and the object `one` in our default program.

It takes in two parameters, `speedL` and `speedR`, and moves the left and right motors at the speeds specified.

The values of `speedL` and `speedR` range from -100 to 100, where -100 is the maximum speed in reverse, and 100 corresponds to the maximum speed in the forward direction.

0 will stop the motors from being spun, but will not actively apply any brakes to stop the motion of the robot.

{{ site.data.alerts.tip }}
You can turn the robot by moving the motors at different speeds. 
<ul>
<li>-100, 100 would turn the robot as hard to the left as possible</li>
<li>100, 50, would turn the robot less sharply to the right, navigating the robot in a circle..</li>
</ul>
{{ site.data.alerts.end }}

## Obstacle Avoidance

```
void brake(byte torqueL,byte torqueR);

one.brake(100,100);
```

The `brake()` function also takes two arguments: torqueL and torqueR.

These values define the braking power of each motor, which ranges between 0 and 100.

0 corresponds to stopping without braking, whereas 100 corresponds to stopping with the maximum braking torque.

### Exercise 4.3.1

- Again, Start by copying the "empty" program from ["Robot Programming Introduction"](/robot_programming_introduction.html) into your Arduino IDE, and saving it in a sensible place.
- Fill in the program so the robot moves when it's started, using `move`, and stops when it sees an obstacle, using `brake`.

{{ site.data.alerts.tip }}
We recommend setting both speeds to 25 for this exercise so you can easily observe the stopping behavior as well as master its usage before crashing your robot into the wall at top speed.
{{ site.data.alerts.end }}

{% include callout_red_cup.html task="[Exercise 4.3.1]" %}

{% include note.html content="Counselors should take students out to the bridge or to a wall in the 3rd floor lab to observe that this behaves properly before proceeding." %}

## Building a Simple Interface Using the LCD and Pushbuttons

```
byte readButton();

one.readButton();
```

The `readButton` function indicates which of the pushbuttons PB1, PB2 or PB3 is being pressed. The function returns an int, with the possible values:

---|---
| 0 | no button is being pressed |
| 1 | PB1 pressed |
| 2 | PB2 pressed |
| 3 | PB3 pressed |

### Exercise 4.3.2

{{ site.data.alerts.tip }}
<ul>
<li>Exercises 4.3.2 - 4.3.5 combined are the largest programming exercise in the camp so far, and the hardest we've asked you to do yet. If you are not sure what this exercise expects, ask the counselors to show you a demo.</li>
</ul>
{{ site.data.alerts.end }}

- Create a new Arduino program

- In this program, print which button is being pressed on the top line of the LCD, "No button," "PB1," "PB2," "PB3."

{{ site.data.alerts.tip }}
Using a switch-statement to identify which button is being pressed will simplify your code.
{{ site.data.alerts.end }}

### Exercise 4.3.3

We're going to begin to create a simple interface that will allow us to control the speeds of the motors.

- Add a global boolean variable to the top of your program. Call it `leftRight`. Set it to `false`.
- In your loop function, make it so that if `leftRight` is `false`, "Left" prints on line 2 of the LCD. If it is `true`, print "Right" on line 2 of the LCD, instead.
- Make it so that pressing PB3 toggles `leftRight` so that if it is `true` it becomes `false` and vice-versa.

At this point, your program should now say which button is being pressed on the top line if a button is currently pressed, and should switch between "Left" and "Right" on the second line whenever you press PB3.

### Exercise 4.3.4

- Add two global variables, `int leftVal` and `int rightVal`.
- Set both to zero at the start of the program.
- Make it so that pressing PB1 increments `leftVal` by 1 if `leftRight` is `false`, and `rightVal` by 1 if `leftRight` is `true`.
- Make it so that pressing PB2 decrements `leftVal` by 1 if `leftRight` is `false`, and `rightVal` by 1 if `leftRight` is `true`.
- Display the values of `leftVal` and `rightVal` on LCD line 1. Remove the code that displays which button is being pressed.

Now your program should allow you to increase and decrease `leftVal` and `rightVal` and select which is changed using the pushbuttons on the robot.

### Exercise 4.3.5

- Use `if` statements, the modulo (`%`) operator, or other logic to limit the range of `leftVal` and `rightVal` to be between -100 and 100.

{% include callout_red_cup.html task="[Exercise 4.3.2, 4.3.3, 4.3.4, 4.3.5]" %}

## Controlling the Robot's Motors

What we're going to have you do now is combine the user interface that you just wrote with the motor code from Exercise 4.3.1.

This will let you try different things with the robot's motors to see how the robot can move and turn, as well as stop before it hits an obstacle.

### Exercise 4.3.6

- Create a new Arduino program combining your UI from Exercise 4.3.5 with the motor code from 4.3.1.
- Your `loop` function should take the user input from the pushbottons at the top of the function.
- At the bottom of the function, you should detect whether or not an obstacle is in front of the robot.
  - If there is an obstacle, the robot should brake with torque 100, 100.
  - If there is not, it should put leftVal and rightVal into the left and right motors, respectively, using `move`.

### Exercise 4.3.7

- Go out to the bridge and try a few different things with the robot's motors.
  - Can you make the robot make a big circle to the right?
  - Can you make it make a big circle to the left?
  - Do you understand why this happens?
  - Can you make it spin in place in both directions?
  - Can you make it go backwards?

{{ site.data.alerts.tip }}
<ul>
<li>Try low values at first. The robot can move faster than you are likely to expect it to move!</li>
</ul>
{{ site.data.alerts.end }}

{% include callout_red_cup.html task="[Exercise 4.3.6, 4.3.7]" %}

## Next Step

Proceed to ["Turn & Push"](turn_and_push.html)
