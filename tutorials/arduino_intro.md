---
title: "Introduction to Arduino"
tags: [arduino]
keywords: arduino
sidebar: tutorials
permalink: arduino_intro.html
---

{% include note.html content="We'll synchronize at the synchronization marker as teams complete the C++ exercises. For now, here's some material to learn about microcontrollers and Arduino." %}

## Microcontrollers

At the heart of your robot, and what you will spend much of the week programming, is an Atmega 328 microcontroller. A microcontroller is like a entire computer on a single microchip. It has storage, a processor, and memory, much like any other computer does.

Microcontrollers are designed primarily to be embedded in other devices. Many devices that you are familiar with have some type of microcontroller driving them.

There are actually two microcontrollers on the Bot'n Roll One. The second is a PIC18F45K22. On the Bot'n'Roll, this comes pre-loaded with all of the software that we want on it.

## Arduino

{{ site.data.alerts.tip }}
<ul>
<li>Open external links in new tabs if you go to them for extra reading. You'll want to get back to the tutorial quickly.</li>
<li>You can do this by right-clicking the link and selecting "Open link in new tab" from the menu that pops up.</li>
</ul>
{{ site.data.alerts.end }}

Arduino is an open-source electronics platform designed around Atmega microcontrollers. You can find more information on Arduinos ["Here"](https://www.arduino.cc/en/Guide/Introduction)

Arduinos makes the previously very difficult-to-enter world of microcontrollers accessible to programmers who already know how to program in C++.

Part of this is by standardizing how pieces interact with the Arduino. Whereas there are many ways to connect devices to an Atmega microcontroller and program them, there are a few *very well documented* ways to do this with many devices on an Arduino.

Another part of this is by offering an extensive API (Application Program Interface) for developers who want to use parts of the microcontroller. The API handles the small parts of interacting with the Atmega microcontroller so developers can concentrate on the problem that they want to solve.

Arduino microcontrollers also are at the heart of a number of projects that enthusiasts at all levels can take on. For instance, ["Adafruit"](https://www.adafruit.com/category/17?gclid=EAIaIQobChMI2LD6vtWl3AIVjYbACh0IvwY0EAAYASAAEgJKDPD_BwE) offers a number of kits based on Arduinos for enthusiasts to assemble and program.

One of my (Justin's) favorite projects for the Arduino microcontroller is building 3D printers. The RAMPS (RepRap Arduino Mega Pololu Shield) board is designed to attach to an Arduino in order to control a 3D printer.

Here are a couple of pictures of mine. Mine is a HyperCube CoreXY.

![HyperCube CoreXY](images/hypercube.jpg)

![HyperCube Owl](images/hypercube_owl.jpg)

{% include callout_synchronize.html comment="People will have the same questions while we go through the basics for the first time. Let's do it together!" %}

## Set up the Arduino IDE

We need to get the library that drives the robot. A library is a collection of software that is distributed to write other software. For instance, video game designers often use graphics libraries that are already written in order to allow them to concentrate on writing the game, rather than the details that are the same from game-to-game. The Bot'n Roll robot comes with a software library, and to use it, we need to install it.

Open up the Arduino IDE.

{% include terminal_command.html command="arduino" %}

Go to the Arduino IDE.

- Navigate to "Sketch -> Include Library -> Add .ZIP Library".
- In the dialog, double-click "exercises/" to open the folder.
- Click BnrOneA.zip and hit OK.

{% include tip.html content="You may get some warnings saying that Bluetooth cannot be used. Don't worry. We're not using Bluetooth." %}
