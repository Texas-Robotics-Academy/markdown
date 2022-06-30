# The Line Follower

In this tutorial, we're going to do quite a lot, and it's going to be challenging. I've given you quite a lot of direction here, so you basically end up with the same program as I wrote, but hopefully figure out how to do it. You're going to need a lot of help from the counselors. This is the hardest program you've written so far this camp. It will be challenging, but that's okay! This is how you learn.

I'm going to tell you what this program does so you can see where this is all going.

The first program that you will write will allow you to use the Arduino serial monitor to see the numbers returned by the line follower. It lets you explore the raw, numerical data that the device sees, and how each number is in a position corresponding to the line. What I've said will make sense once you've tried it out.

The second program that you write will allow you to **threshold** the data coming off of the line follower, to determine what is a line and what is not. It will use the LCD on the robot to print asterisks wherever the line is under the line follower, and dashes wherever there isn't.

That will look something like this.

`----**----------`

If it looks like that, there's a line most of the way to the left of the robot.

`**--------------`

If it looks like that, there's a line all of the way to the right of the robot.

`--------------**`

Under the line that looks like that, it will print the number that is the value of the threshold. You will learn about thresholds in this exercise.

My program says this right now.

`----**----------`

`10`

Just kidding. I want you to find the threshold for yourself. Mine is much bigger than 10.

## Back to the Bot'n Roll Library

The `BnrOneA` class still has a significant amount of functionality that we haven't yet touched, one of those is the use of the analog-to-digital converter

### `int readAdc(byte), int readAdc#()`

The PIC microcontroller has an 8-channel analog to digital converter on it. This allows us to hook electronics components up to the robot and read information off of them. The data comes in as analog data; that is to say, electrical voltages. An **analog-to-digital (ADC)** converter converts these voltages to digital information, allowing us to use it in our computer programs.

{{ site.data.alerts.tip }}
- You can think of the analog data sort of like a dimmer switch on a light. More electricity makes the light brighter. The problem for the microcontroller is that it doesn't work with voltages as analog circuits do. It works with binary, discrete representations. The **analog-to-digital (ADC)** will convert the voltage into a number that can be understood by the computer.
{{ site.data.alerts.end }}

The PIC has 8 ADC channels, which can be accessed by calling either the corresponding `readAdc#` function, or by providing 0-7 to `readAdc`. 

## The Line Follower Device
Look under your robot at the line follower. It has 8 little black blocks on it. These blocks are used to detect how much light us coming up off the ground to the robot.

Each of those blocks is hooked up to a separate channel of the ADC. Consequently, the ADC will read each of them and return a value between 0-1023.

## Exercise 6.1.1

### The Line Follower Test Target

- Get a "Line Test Target" from a counselor.

### Tips on Serial.print

{{ site.data.alerts.tip }}
For this exercise we're going to use a bit of the Arduino IDE that we haven't used in a while, which is the Serial Monitor. If you don't recall how to open this up, look it up in the **Robot Programming Introduction**.
{{ site.data.alerts.end }}

- `Serial.print` is used to send text data on the USB port.
- You can see what has been printed using the Serial Monitor in the Arduino IDE.
- `Serial.print(number)` will print a number.
- `Serial.print(" ")` will print a space.
- `Serial.println() will give you a new line.

### Program the Exercise

For this exercise we want you to read the values off of the line follower, while running it over the line target. You're going to need to write a short program to do this.

Here's what your program should do.
- Read each of the values from the line follower using the `readAdc` function(s).
- Print each value onto the USB port using the `Serial.print` functions.
- Print a space following each value from the line follower.
- Print a new line at the end of the 8 values.

When you hook this up, the numbers are going to scream past on the screen really quickly, so we suggest adding a `delay` after the for loop to make everything much easier to read.

{{ site.data.alerts.tip }}
- The easiest way to implement this is with a for loop and the `int readAdc(byte)` function.

- Count from 0 to 7 using the for loop.
- Inside the loop, read the value in the corresponding ADC channel.
- `Serial.print` that value and a space.
- After the for loop, use `Serial.println`.
{{ site.data.alerts.end }}


### Try the Line Follower

- Move the line target around under the robot.
- You should notice that the numbers where the black line is present are different from the numbers where there is no black.
  - How are they different?

{{+}}Exercise 6.1.1, 6_1_1{{+}}

## Thresholding

If you did the last exercise properly, you should have noticed that ABOVE some value, you could assure that the number being returned by the line follower was the the line being picked up. Beneath some value, what you saw was the white paper reflecting light back.

The difference between the region where the line was and the region where there was no line is called a **threshold**. We are going to use a threshold to determine where the line is.

{{ site.data.alerts.tip }}
Also, weirdly, the line follower seems to pick up the shadows of the wheels. Don't worry about it, and simply realize that even when you account for the wheels, the threshold is still higher than the value for the shadow.
{{ site.data.alerts.end }}

Uh-oh! We're going to have you follow a line out on the bridge, but the lighting is different and the paper is different in the lab! What we'll do to account for this is write a small user interface where you can tune your threshold. While we're at it, we'll also experiment with the line follower and the LCD, and learn a bit about strings in C++.

## Exercise 6.1.2

The next few exercises will build up to a small user interface that will allow you to see the line the way that your robot sees it!

### In C++, Most Text is Just Special Integers
- Write a quick function, call it `void printAsterisks()`.
- Have `loop` call `printAsterisks`.

{{ site.data.alerts.callout_code_div }}
```cpp
void printAsterisks() {

}

void loop() {
  printAsterisks();
}
```
{{ site.data.alerts.end }}

{{ site.data.alerts.tip }}
It's going to be tempting to put a `delay` in there somewhere. Even some of the counselors will tell you to do this. Do yourself a favor and resist that urge. Your program will work better and look better if you avoid this.
{{ site.data.alerts.end }}

There's a type that we didn't tell you about way back in ["Simple Math and User Input"](/simple_math_user_input.html) called `char`.

`char` stands for **character**.
Each `char` is 1 byte, meaning that it can represent 256 different numbers.
Each `char` is `unsigned`, meaning that it cannot be negative.

One way to represent text is called a C string. This is different from a C++ `string`. A C string is an array of type `char`.

Every number from 0-255 is associated with a unique, printable character. This is called **ASCII**.

{{ site.data.alerts.tip }}
- ASCII - American Standard Code for Information Interchange
- There's a good article on Wikipedia about learning ASCII if you really want to, but it won't be especially relevant to what we're doing here, so, save that for after camp!
{{ site.data.alerts.end }}

- Remember the `one.lcd1` command? Use that in your program to print 2 asterisks ("*") on the top line of the LCD on your robot.
- Now try it using a C string.
  - Make a global variable to store your C string in. Call it `lineUI`.
  - Make `lineUI` 17 chars long.
  - Make a `for` loop to fill `lineUI`.
  
{{ site.data.alerts.callout_code_div }}
```cpp
void printAsterisks() {
  for(int i = 0; i < 16; i++) {
    lineUI[i] = '*';
  }
  lineUI[16] = 0;
  one.lcd1(lineUI);
}

void loop() {
  printAsterisks();
}
```
{{ site.data.alerts.end }}

- What the heck? You can do that?
  - Yes! Single quotes surround a **character-literal** in C.
  - Just like a string can be surrounded in double-quotes (which is called a **string-literal**), a single character can be surrounded in single-quotes.
- You probably also noticed that I set `lineUI[16] = 0;`
  - C strings are **null terminated**. This means that you put a 0 at the end of the string to mean that the string is done.

{{ site.data.alerts.tip }}
Null termination allows us to have shorter or longer strings stored in the same memory. This means that if we only wanted lineUI to be 8 characters long, we'd just put a zero in `lineUI[8]`.
{{ site.data.alerts.end }}

- Go ahead and run the program from the example above. Don't forget to add any declarations and things that I didn't put into the code snippet!

### Modify the `for` Loop from above

In our UI, what we want is for the top line to show us where the line is. Eventually, there will be asterisks where the line is, and dashes everywhere else.

However, we run into a problem. There are 8 sensors on the line sensor, and 16 characters on the top line. So, we'll want 2 asterisks for every sensor on the line follower. If we have that, and ONLY asterisks turned on for each sensor on the line follower that sees a part of the line, then we will be able to see the line the way that the robot sees it!

- Modify the `for` loop from the example above to **iterate** through the loop 8 times so that only 8 asterisks show up on the LCD.
  - Don't forget to change your null terminator.
  - Your for loop should now count from 0-7. `int i = 0; i < 8`!
- Modify the `for` loop so that it only iterates 8 times, but still prints 16 characters.
  - Do this by making every time it iterates through the loop insert 2 asterisks into `lineUI`.
  - You can do this by multiplying `i * 2` when you fill in `lineUI`
  - That, however, will skip ever other entry in `lineUI`, so, make it also fill in `i * 2 + 1` with an asterisk every time it iterates through the `for` loop.
  - Try it out!

{{+}}Exercise 6.1.2, 6_1_2{{+}}

## Exercise 6.1.3

Now we're going to write another UI. This should all go into your current program.

- Add a global variable. Make it an integer. Call it `thresh`. Set it to zero either at initialization or in `setup`.
- In `printAsterisks` print the value of `thresh` on line 2 of the robot's LCD.
- Add some code to `loop` that responds to button presses.
  - When PB1 is pushed, add 10 to `thresh`.
  - When PB2 is pushed, subtract 10 from `thresh`.
- Try it out. The number on the second line should very quickly rise when pressing the top button and very quickly drop when pressing the lower button.

{{+}}Exercise 6.1.3, 6_1_3{{+}}

## Exercise 6.1.4

Now we're going to make it so you only see where the line is under the line follower, allowing you to see the line the way that your robot does.

- Make a global array of type `int`. Make it 8 elements. Name it `adc`.
- Modify `loop` so that it reads the ADC using `one.readAdc`.
  - Use a `for` loop so that it fills the `adc` variable.
- Modify the `for` loop in `printAsterisks`.
  - Every time `adc[i] > thresh`, it should put 2 asterisks.
  - Every time `adc[i]` is not ` > thresh`, it should put 2 dashes.
- Run your program. Put the line target under the line follower. Push the up button until there are only asterisks under the line follower sensors that are over the line, and dashes everywhere else.
- Move the target around and see how the robot can now "see" the line.
  - Ideally, you only see the line in one place on the LCD, and it is only 2 asterisks wide.

{{+}}Exercise 6.1.4, 6_1_4{{+}}

{{-}}Line Following, in_person/robot_line_following.md, Next{{-}}