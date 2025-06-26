# Exercise 12: Encoders

## Exercise 12.1: Starting with Encoders

(Rotary) encoders measure the motion of a motor. They make "ticks" in an encoding called "quatrature" to measure how far the motor has turned.

Each wheel on your robot is equipped with an encoder.

You can read them like this.
- int encL = one.readAndResetLeftEncoder();
- int encR = one.readAndResetRightEncoder();

Note the name of the method. It reads the value off of the encoder and ALSO resets the count to zero.

There are some complexities here. The robot uses communication between the PIC microcontroler and the Atmega (Arduino). The robot uses a "quadrature counter" to read the encoder "pulses," counting the turning of the motor. At any given trip through loop, the encoder may - inaccurately - read 0 rather than the true current encoder value.

Let's try messing with the encoder:

Make a class called RPM.
- Give it attributes:
  - int _encL[4]; int encR[4];
  - int _iteration;
- Give it methods:
  - void runMotors();
  - void printDisplay();
  - void buttonPress(byte button);
- Implement this stuff:
  - Make buttonPress and display control the speeds of the motors (ranging from -100 - 100).
  - Display the speeds of the left and right motors on LCD 2.
  - Make runMotors() actually change the speeds of the motors.
  - Also make runMotors call one.readAndResetLeftEncoder() and one.readAndResetRightEncoder()
  - Put the encoder counts in _encL[4] and _encR[4], using _iteration to keep track of iterations (0-4), looping back through and filling in _encL[0] and _encR[0] once the arrays are full.
  - Compute the sum of the encoder readings, and display on LCD1 in printDisplay()

So, this class should compute how far the motor is turning every 4 iterations through loop() in encoder ticks!

## Exercise 12.2: Computing RPMs
The encoder has 2250 counts per turn. Meaning, for every full rotation of the motor, the encoder will make 2250 "ticks."

There is an arduino function called millis(). It counts how many milliseconds (1000s of a second) have passed since the arduino has been turned on.

Add an attribute to RPM:
- int _millis[4];

Modify runMotors() to record the value of millis() in _millis at every iteration, when you record _encL and _encR.

- Use these values to modify runMotors() and printDisplay() to show "Revolutions Per Minute" (RPM), rather than simply encoder ticks.

## Exercise 12.3: Computing Meters per Second
The diameter of each wheel is 63mm
- Modify runMotors() and printDisplay() to show how fast the vehicle is moving in meters per second.