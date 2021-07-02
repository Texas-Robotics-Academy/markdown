---
title: "Less Used Functions"
tags: [robot programming]
keywords:
sidebar: tutorials
permalink: less_used_functions.html
---

## `minBat`

`void minBat(float batmin);`

Let's suppose that you only want the robot to operate if the batteries are charged above a certain threshold. Maybe the robot is racing, or is about to take on a long task. This function will prevent the robot from operating and display an error message if the battery is too low.

## `readBattery`

`float readBattery()`

This returns the number of volts currently output by the battery. You can use this to determine how charged your robot is.

## `setPID`

`void setPID(int kp,int ki,int kd)`

The motors on the robot use what is called PID (proportional-integral-derivative) control to control the speeds at which the motors move. This is implemented on the PIC microcontroller. The ints `kp`, `ki`, and `kd` are called the <b>PID gains</b>. They are the parameters for PID control. The robot has good defaults for these, so there really isn't a reason to tamper with them. Setting different values may cause the robot to move faster, or it may cause it to accelerate and decelerate wildly, making your robot difficult for you to control.

{{ site.data.alerts.tip }}
Interested in learning more? <a href="http://students.iitk.ac.in/roboclub/lectures/PID.pdf">HERE</a> is a brief tutorial.
{{ site.data.alerts.end }}

## `readIRSensors`

`byte readIRSensors()`

The difference between `obstacleSensors` and `readIRSensors` is a small one.

The robot automatically looks for obstacles every 20 milliseconds. `obstacleSensors` returns the result.

`readIRSensors` sensors, instead, asks the robot what the status of the IR sensors is right now.

In general, you're going to want to use `obstacleSensors`, and the difference between the two functions is not that significant to us right now.

## `void servo#(byte position)`

In theory, the robot can control two servos. In practice, it has no servos connected to it. There are more details on using this functionality in the software manual.
