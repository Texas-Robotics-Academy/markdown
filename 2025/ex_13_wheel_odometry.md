# Exercise 13: Wheel Odometry

Wheel odometry is measuring how the robot moves, precisely, using measurments of how far the wheels turn.

## Exercise 13.1: Bang-Bang Control

Bang-Bang control works like this. Have we reached where we're going yet? No? Throw the motors all the way forward until we have. Oh, we're past it? Throw them all the way back until we're back where we're trying to go.

In robotics, motion doesn't oven work like our race. We want the robot to move to precise positions (possibly quickly).

- Write a class called EncoderCountedMotion
  - Methods
    - void setMotionGoal(int goalCountsL, int goalCountsR)
      - This should set how many encoder counts until the robot has reached its motion goal for both the left and right motors.
      - It should also call one.readAndResetLeftEncoder() and one.readAndResetRightEncoder(), so the encoders are zeroed out
    - void runMotors()
      - This should:
        - Compute how many encoder counts remain until the motion goal is met. Remember the lessons from the RPM class in how to manage this.
        -  If a motor has not yet reached its required number of encoder counts, it should move forward.
        -  It it has surpassed its required number of encoder counts, it should move backward.
        -  The motors should move at a constant speed, so +-10 or some other number, until they hit the motion goal. I just use 100.
    - void printDisplay()
      - Should show:
        - The interface to set required encoder counts. I just put the numbers for the left and right motor on LCD 2.  These should not be input directly into setMotionGoal, but should be recorded and stored. setMotionGoal() should be called in a "Go" operation, that starts the robot.
        - A "Go" operation, that takes the encoder counts, and provides them to setMotionGoal()
        - How many encoder counts remain to reach the goal on LCD 1.
    - void buttonPress()
      - Should provide a visual interface to adjust the encoder counts and call the Go operation.
- Instantiate your class in a global variable. Mine is EncoderCountedMotion encoderCountedMotion;
- Call your runMotors(), printDisplay(), and buttonPress() methods in your loop() method.
- If you started writing this program from your RPM program, don't forget to comment out the RPM methods in loop().

Now, if you put your robot on the ground, call this with a reasonable value for each motor (let's say, 5000), you should see the robot continually undershoot and overshoot it; rocking back-and-forth on the ground. You've made a precise motion algorithm, but bang-bang control doesn't quite cut it for actual precise motion.

{{+}}Exercise 13.1, 13_1{{+}}

## Exercise 13.2: PID Control

Let's revisit PID control.

PID controllers don't normally have a kC. We added that to assue that the robot always moves forward down the race track.

Clamping is assuring that a variable does not surpass a maximum or minimum value.

- Implement a class called ClampedPID
  - It should have these attributes as floats:
    - _kP, _kI, _kD
  - Set them in your class's constructor.
  - It should have this method: float computeControlSignal(float error)
    - computeControlSignal should compute the PID control signal, as we did in the PID control exercise (Exercise 10), and the Race.
    - Remember.. no kC!
    - It should clamp the output to be between -100.0 and 100.0

Unlike in our race, we can forgo putting the PID control parameters into the robot's menu, but if you like, you probably understand how to do that now.

- In your EncoderCountedMotion, instantiate a ClampedPID object.
- Instead of putting a constant speed into one.move(), call ClampedPID's computeControlSignal() method to get the speed for the left and right motors.
  - Your error is now the number of remaining encoder counts (positive or negative) to arrive at your motion goal.

Note that your encoder counts do not range from -1.0 to 1.0. Your PID gains are likely to be FRACTIONAL.

Tune the gains until you are able to stop almost exactly at your motion goal, and the robot actually stops moving at the end of a "Go" command.

{{+}}Exercise 13.2, 13_2{{+}}

## Exercise 13.3: Moving to Real Measurments

Use what you know about the diameter of the wheels to convert setMotionGoal() to take floats as parameters and move in meters rather than encoder counts. You should still INTERNALLY in the class take encoder counts. This is just how we treat the parameters to setMotionGoal().

- Convert setMotionGoal() to meters
- Convert your menu to meters
- See how close you can get to the robot actually stopping at 1.0 meters.
- Make it make precise circles, like a 1/4 circle with a diameter of 1.0 meters.