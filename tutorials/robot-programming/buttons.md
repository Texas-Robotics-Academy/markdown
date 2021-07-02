

## `readButton`

`byte readButton()`

This allows you to use the buttons on the right-hand side of the LCD screen on your robot.

Value    | Means
--------|-------------
0	| No button is pressed
1	| PB1 is pressed
2	| PB2 is pressed
3	| PB3 is pressed

If more than one button is pressed, the value of the lowest pressed button is returned.

### Exercise 4.2.6

In some of the upcoming exercises, you'll need to make your robot select different settings which the user can control using the buttons on the robot. To prepare you, we'll quickly try out the buttons.

- Use a switch statement to print out which button has been pressed on the LCD of the robot.
- "No button is pressed," "PB1 is pressed," "PB2 is pressed," or "PB3 is pressed," as in the table above.

### Exercise 4.2.7

We also want you to understand global variables, so let's try a variation on this.

- Use a global variable to store the value of the last button which was pressed.
- On LCD line 1, display "PB1," "PB2," or "PB3."
- On LCD line 2, display whether or not a button is currently being pressed.

{% include callout_red_cup.html task="[Exercises 4.2.6, 4.2.7]" %}
