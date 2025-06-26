# Exercise 6: Switch Statements


## Exercise 6.1:

cd into the ex6 directory.

Write a short program.
- Use cin to take in a value.
- Use a switch statement on that value:
  - If it is 0, print "Zero."
  - If it is 1, print "One."
  - If it is 2, print "Two."
  - If it is 3, print "Three."
  - If it is none of these, print "Other."

{{+}}Exercise 6.1, 6_1{{+}}

## Exercise 6.2:

Save ex5 as ex6_2.

- Detect obstacles
  - Make a variable called obstacleDetection.
  - Make a variable called threshold.
  - Use one.readLeftRangeSensor(), one.readRightRangeSensor(). Store the values of both in variables, leftO and rightO. (Calling them again can change the value they return.)
  - If neither is > threshold, make obstacleDetection = 0.
  - If only left is > threshold, make obstacleDetection = 1.
  - If only right is > threshold, make obstacleDetection = 2.
  - If both are > threshold, make obstacleDetection 3.
- Print on LCD 1:
  - Use a switch statement that tells us which sensor is activated: left, right, both, none - on LCD 1.
  - "No obstacle" - When there is no obstacle.
  - "Left" - When there is an obstactle on the left side.
  - "Right" - When there is an obstacle on the right side.
  - "Both" - When both obstacle sensors have been activated.
  
- Use one.readButton().
  - Use a switch statement that tells us which button is being pressed: none, 1, 2, 3.

{{+}}Exercise 6.2, 6_2{{+}}

{{-}}Exercise 7: Controlling the Motors, 2025/exercise_motors.md, Next{{-}}