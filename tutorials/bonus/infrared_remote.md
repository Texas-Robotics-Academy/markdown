---
title: "Infrared Signals to the Robot"
tags: [c++ programming]
keywords: Infrared
sidebar: tutorials
permalink: infrared_signals.html
---

## Introduction

The obstacle detection on the robot is performed through the use of infrared LEDs and infrared phototransistors on the front of the robot.


It is possible to turn off the infrared LEDs on the front of the robot with the `obstacleEmitters` command.

One use of this would be to prevent them from interfering with the phototransistors so you could read them for other purposes. Here, we list a couple of ideas for you to implement based on the concept of turning them off.

### Remote Control

By reading the IR Sensors on the front of the robot, but not using them for obstacle avoidance, you can potentially control the robot with a standard infrared remote control. Doing this will require you to master portions of the Arduino Library and functions of the Atmega 328 microcontroller that we have not introduced in the tutorials, so this poses, potentially, a significant challenge in implementation. We have an infrared remote that you can borrow for these purposes.

[//]: # ("### Race Start One of the optional challenges is to race your robots using the line follower in order to try to get the best time, but it is possible to do a head-to-head robot-vs-robot race. We'd need to set up a lot of additional infrastructure, and you could help us to build that infrastructure by writing the software that would allow the robots to wait for an infrared signal to start the race. If you take this on, you can also help us to design a suitable race course for the robots to challenge each other on.")
