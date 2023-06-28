#Line Following
In this tutorial, you're going to make the robot follow a line on the ground.

At the end, you will be invited to race the other groups.

Awesome.

## Exercise 7.1.1 - Automatically Finding the Line

In the previous tutorial, you found the line by setting a threshold, but you can automatically find the line as well, but choosing the line sensor with the highest value.

We think that you're ready for a slightly harder tutorial. So I'm just going to tell you how this is done.

- Check the first ADC channel.
- Store its value in a variable.
- Use a loop to check each ADC channel.
- If a channel has a higher value than the one stored, store that value.
- Always store the channel corresponding to the highest value as well.
- Put this into a function.
- Test that your detector works by using the `printAsterisks` function from the previous tutorial.

{{+}}Exercise 7.1.1, 7_1_1{{+}}


## Exercise 7.1.2 - Describing Where the Line Is

If the line is in the channel all the way to the left, the method above should give you 0.

If the line is in the channel all the way to the right, the method above should give you 7.

Right in the middle would be 3.5.

- Write a function that scales the output of the automatic line finding to range from -1 to 1, using the facts listed here.
- Print your asterisks on the first line of the LCD, and the value returned by this function on the second line.

{{+}}Exercise 7.1.2, 7_1_2{{+}}

## Exercise 7.1.3 - A Proportional Controller for Line Following

In Exercise 7.1.2, you calculated which channel (0-7) the line is closest to. This is called the **potential**. Let’s combine this concept with a linear formula (`y = mx + c`), so we have a simple linear controller – called a proportional controller.

This will look something like this: 

- The potential computed in Exercise 7.1.2 is used to steer the robot. This is the **m** value in `y = mx + c`.
- The **c** value refers to speed. The robot should default to going forward at a constant speed.
  - Your constant term in your program will look something like this: `one.move (constant, constant)`
- The **x** value is the how much the robot corrects itself during its course – called the proportional gain (**K_p**)
- So now think of the formula as something like this: `speed = c + mx`, `speed = c = mx`.

Write a program that creates a proportional controller, using the facts stated above. Create an interface using the push buttons to be able to manually adjust the **K_p** and **constant** values on the robot. Take your robot out to the bridge and try it on our race course using the proportional controller. Adjust **K_p** and **constant** values as needed.

{{+}}Exercise 7.1.3, 7_1_3{{+}}

## Exercise 7.1.4 - A Proportional Derivative (PD) Controller for Line Following

You probably noticed that your robot jerked around when using the proportional controller. This is known as "bang-bang control," and we try to prevent it from happening.

We can improve on our control by adding a **derivative** term. The derivative term approximates the rate of change at a particular point in a curve by subtracting one point from another along the curve, and finding the slope of the tangent line.

Think of your robot as sampling two points on a curve, and the angle that you want the robot to steer at as the tangent line on the curve.

What this all means is that you can take the potential calculated in Exercise 7.1.2 at your current time step, subtract the potential computed at the *previous* time step (a time step being one execution of your `loop` function) and arrive at the derivative that you want.

{{ site.data.alerts.tip }}
If this doesn't make sense to you, get a counselor to help you. If it doesn't make sense to them, get them to get Justin, and make them listen to the explanation too.
{{ site.data.alerts.end }}

You now have 3 (adjustable) terms for your controller:
- **Constant gain** (`K_c`).
- **Proportional gain** (`K_p`).
- **Derivative gain** (`K_d`).

And two calculated terms:
- **Potential** (p)
- **Derivative** (d)

The formulas for your controller now look like `K_c + (K_p * p + K_d * d)` `K_c - (K_p * p + K_d * d)`

- Implement this on your robot.
- Add K_d to your user interface, so it is adjustable using push buttons.
- Take your robot out to the bridge and try it on our race course using the PD controller.

{{+}}Exercise 7.1.4, 7_1_4{{+}}

## Exercise 7.1.5 - A Proportional Integral Derivative (PID) Controller for Line Following (Optional)

Probably the best known controller is the PID controller, where I stands for **integral** - area under the curve.

In practice, you can compute your numerical integral by adding up your errors over time to arrive at area under the curve for your potential.

- **Constant gain** (`K_c`).
- **Proportional gain** (`K_p`).
- **Derivative gain** (`K_d`).
- **Integral gain** (`K_i`).

- Implement this on your robot.
- Add `K_i` to your interface.
- Take your robot out to the bridge and try it on our race course using the PD controller.

{{+}}Exercise 7.1.5, 7_1_5{{+}}


{{-}}Race, in_person/robot_race.md, Next{{-}}




