# Exercise 9: The Line Sensor

{{ site.data.alerts.note }}
Obstacle sensors are neat, but in this exercise, you'll read and threshold the line sensor. The techniques you'll use are basic computer vision techniques.
{{ site.data.alerts.end }}

## Exercise 9.1: Arrays
The line sensor uses an array, so we want you to practice arrays first.

Look in ex_9. There is already an ex9_1.cpp file in there for you to edit.

- Write a for loop in main.
  - Have it count from 0-9 on "i" (for(int i and so on))
  - Use cout to display "i" at each iteration of the loop
- Make an array of ints. Use the for loop to fill it with numbers 0-9.
- Use the for loop you just wrote to fill it with the numbers 10-19
- Use a second for loop to display the contents of your array.

{{+}}Exercise 9.1, 9_1{{+}}
  
## Exercise 9.2: Reading the Line Follower and Examining its Output

Open ex9_2 in arduino.

There is a class called LineFollowerInterface, with two methods:
- void readLineFollower()
- void printSerial()

You can read the line follower sensors using one.readAdc(const byte adc_channel);

There are 8 channels. They are connected to the line follower.

There is a variable:
- int _adcVals[8]

Do the following:
- In readLineFollower() implement a for loop that reads each adc channel into the 8 indices of _adcVals.
- In printSerial use Serial.print() and Serial.println()
  - Print each value in _adcVals on the same line, with a space in between.
  - Print a new line using Serial.println()

Ask a PA for a line target. Turn on the robot, while connected to the serial monitor. Look at the values printed by the robot onto the serial monitor. Slide the line target under the robot. You can see how this changes the values of the line follower.

{{+}}Exercise 9.2, 9_2{{+}}
  
## Exercise 9.3: Adding an LCD Interface to the Line Follower

- Save ex9_2 as ex9_3.

Edit LineFollowerInterface. Add two attributes.
- char _asterisks[17]
- int _threshold

Add a menu, like you had for your motors. You could start by copying the menu from Exercise 8_3. So, in LineFollowerInterface. You'll probably want two similar class methods:
- void buttonPress(byte button) - Which you use to adjust _threshold up and down.
- void printScreen() - Which you display things. Display "Thresh: " & _threshold on LCD 1.
- _threshold should be adjustable between 0 and 1000 (This replaces your void printMenu() in previous examples.)

Let's write a function called void computeAsterisks() which shows which line sensors are above the threshold.
- Your LCD is 16 characters wide.
- Use a for loop.
- For each entry in _adcVals where _adcVals[i] > _threshold, put two '*'s in _asterisks.
- For every other entry in _adcVals, put two '-'s in _asterisks.
- For instance, if your loop looks like for(int i = 0; ...) put a '*' in _asterisks 2\*i and 2\*i + 1.
- Put a 0 in _asterisks[16]
  - This works because this is a "C-Style" string rather than a "C++-Style string" We will discuss this in lecture.
- Add a call to your LineFollowerInterface.computeAsterisks() in loop().
- Edit printScreen() to print your asterisks on LCD 2.

Now, run your program and put the robot on top of the line target to see how it looks on the LCD. By adjusting the threshold, you should be able to make it so you see asterisks on the LCD base on where the line follower is over the line.


{{+}}Exercise 9.3, 9_3{{+}}
  
## Exercise 9.4: Finding the Max of the Line Follower

- Save ex9_3 as ex9_4.

Add a function void findLine()
- Using a for loop, find the maximum value of _adcVals.
  - Store the highest value you've seen so far in int maxVal
  - Store the index of the highest value you've seen so far in int maxIndex
  - Store the value at _adcVals[0] in maxVal before entering your loop
  - Store 0 in maxIndex
  - Use the for loop to check the value at i against maxVal, then store maxVal and maxIndex accordingly if it is greater than maxVal.
  - Add an attribute to your class, int _lineIndex;
  - Store maxIndex in _lineIndex at the end of findLine()

- Modify computeAsterisks() to put '**' only at _lineIndex, and '--' everywhere else.

- Add an attribute to your class, float _linePotential.
- Modify findLine() to compute _lineIndex. _lineIndex should range from -1 - when the line is all the way to the left, and _lineIndex = 0; to 1 when the line is all the way to the right, and _lineIndex = 7. Figure out how to compute this.
- Modify printScreen() to print _linePotential on LCD 1, and the asterisks on LCD 2.

{{+}}Exercise 9.4, 9_4{{+}}

{{-}}Exercise 10: PID Control, 2025/exercise_line_following.md, Next{{-}}