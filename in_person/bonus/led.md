---
title: "Using LEDs"
tags: [LEDs]
keywords: LED
sidebar: tutorials
permalink: led.html
---

Want to add some flair to your robot? Want to do a quick celebration when your robot completes its task or gets to the finish line? Want to indicate the robot's status in some highly-visible way? Then LEDs are probably your first stop.

{% include note.html content="We have purchased enough LEDs for each group to get 10 LEDs for their robot. If it is close to the end of the week and not all of the LEDs have been used, we can give groups extra at discretion." %}

## Getting an LED strip

For our camp, we have purchased self-adhesive strips of WS2812B LEDs. These are full-color LEDs with up to 256 possible values per red, green, and blue channel.

The LEDs are mounted on a flexible printed circuit board in a strip that is 1cm wide, at a spacing of 1 5/16th inches.

The strip can be cut in order to separate the LEDs from each other.

{{ site.data.alerts.tip }}
Have a camp staff member assist you by showing you how the strip is to be cut, as cutting it incorrectly can ruin sections of the strip.
{{ site.data.alerts.end }}

{% include note.html content="You will need camp staff to help you get the strip anyway. Use your red cup to get help." %}

## Attaching the LED strip to the robot

You will need to solder wires to the LED strip in order to attach it to your robot. Ideally, you will also attach a resistor, in order to limit the current going to the strip.

### Choosing a resistor
Here's some quick math for you to solve for us to get started.

Each of these LEDs has been experimentally validated to draw about 33.5 mA (milliamps) of current (though people often cite 50 or 60 mA). The data pins circuit on the Arduino board, which you will connect it to, is a 5V circuit. You should attach a resistor to the LEDs to assure that they get the correct amount of current (though, the board will never generate enough current to ruin your LEDs, so, you can feasibly get away without this if there are no more resistors of the correct size available).

Ohm's Law tells us how big of a resistor we need. It says V = I * R. Voltage equals current times resistance, where resistance is measured in Ohms, and current is measured in Amps.

- If each LED draws 33.5 milliamps, and you have 14 (or however many) of them. How much current will you have?

- The LEDs will be connected to a 5V circuit on the board.

- Using Ohm's Law, how big of a resistor do you need?

### Soldering the LED strips

- Get a member of camp staff to help you set up a solder station on the bridge so you can solder wires to the strip.

{{ site.data.alerts.tip }}
Be careful! Flexible PCBs are thinner than the thick plastic PCB that you were soldering to. It is easy to damage the strip!
{{ site.data.alerts.end }}

There will be 3 lines on your strip +5V, GND, and Data.

- Connect one wire to each, with enough length to reach the following headers on the Bot'n Roll. 5V, Pin 7, and GND.

{{ site.data.alerts.tip }}
You may need to cut the LEDs apart to achieve the placement that you would like along your Bot'n Roll. If this is the case, you will need to solder together the pads at either side of this cut.
{{ site.data.alerts.end }}

- On the wire going to Pin 7 (Data), you should solder your resistor.

### Connecting the LEDs

- Connect the wires corresponding to +5V, GND, and Data, to 5V, GND, and Pin 7, respectively.

## FastLED
There are a number of good options available for controlling your LEDs, but we're going to direct you to [FastLED](http://fastled.io/).

### Getting the Library

- Download the library as a zip file from [here](https://github.com/FastLED/FastLED/archive/master.zip).
- Unzip the library
- Rename FastLED-master to FastLED
- Sketch->Import Library->Add Library, and add the FastLED directory

### The Basics
They have a quick-start quide that documents things just as well as we can, so you can find that [here](https://github.com/FastLED/FastLED/wiki/Basic-usage), but the basics are below.

- In the top of the file, add `#include <FastLED.h>`, `#define DATA_PIN 7`, and define NUM_LEDS to be the number of LEDs on your strip.
- Create an array of datatype `CRGB leds` with the size of the number of your LEDs. This array is what you will modify to alter the color of each LED. 
- Within the setup function add the following: `FastLED.addLeds<WS2812B, DATA_PIN, GRB>(leds, NUM_LEDS);`. 

In order to manipulate the LEDs, you simply modify the contents of the CRGB array. For example, to change the color of the first LED to green, we do `led[0].setRGB(0, 255, 0);`. For the RGB values, you can choose a value from 0 to 255.

{{ site.data.alerts.tip }}
Click [here](https://www.w3schools.com/colors/colors_rgb.asp) for an RGB color picker.
{{ site.data.alerts.end }}

{{ site.data.alerts.tip }}
Another way to choose colors is by using one of the many predefined colors, which you can find listed at this [link](https://docs.google.com/document/d/1QY85vLz8qK-xxumCuDploXaDOspO0OfxWeie8CQJsLI/pub). To set the color using this method, you do the following `led[0] = CRGB::AntiqueWhite;`, where you can replace the words after CRGB:: with the color you want.
{{ site.data.alerts.end }}

Although these changes are made to the LED, the only way you can visualize the changes you made to the LED, you must do `FastLED.show()`. Once you upload the code to your robot, you should then be able to see your code work.

## LED Challenges

Feel free to get creative with your LEDs, but here are a few ideas to start with:

- Place the LEDs in a ring around your robot. Use them to display the direction that the robot will go in when doing other things. Write a function controlling the direction that your robot drives in, and have the LED display happen inside this function. Then, use this function whenever you turn your robot in any challenge or exercise.
- Program a "celebration" for when the robot completes a task, where it flashes its LEDs.
- When solving the maze, program the LEDs to always point towards the goal, once it has been found, or always point in the direction that the robot will turn next when coming to an intersection.

