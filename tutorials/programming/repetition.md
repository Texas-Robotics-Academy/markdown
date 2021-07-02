---
title: "Repetition"
tags: [c++]
keywords: c++
sidebar: tutorials
permalink: repetition.html
---

Sometimes we want our code to execute multiple times. It would be really unfortunate if we had to keep typing the same exact lines of code again and again—what if we didn't know exactly how many times we wanted the code to repeat? Fortunately, we have loops to help us out. A loop is a section of code that the computer runs over and over again until it reaches some stopping criteria. There are two kinds of loops that we will work with: `for` loops and `while` loops.

## For Loops

A `for` loop repeats code for a specific number of times. If you know exactly how many times you want some lines of code to repeat, you'll want to use this type of loop. For example, let's say we want to print "Hello World" five times. We could write the following `for` loop:

```cpp
for (int i=0; i<5; i++){
   cout << "Hello World\n";
   //more lines of code can go here
}
```

This will print:

```
Hello World
Hello World
Hello World
Hello World
Hello World
```

Let's dissect this code

We begin with the word `for`, which tells the computer that we have a for loop.

Then, inside the parentheses, we define how many times we want the loop to run.

The first phrase, `int i=0;`, defines the loop variable, which is the variable whose value dictates how many times the loop executes.

We tell the computer that the loop variable will be an integer named i, and that it will begin by being equal to 0.

The second phrase, `i < 5;`, is a logical expression that works just like those we saw in the last section—when used in loops, the computer will keep executing the loop as long as the expression is true.

In this example, the computer will keep looping as long as i is less than 5; when `i` is greater than or equal to five, it will stop.

The third phrase, `i++`, tells the computer how to modify the loop variable. The shorthand `i++` means that i will increase by 1 every time the loop runs.

Then, inside curly braces, we put all the code that we want to execute each time the loop runs.

Now we will look at another example. Say we want to count from 0 to 9, and we want to print out the number each time. We can easily use a loop to do this:

```cpp
for (int i=0; i<10; i++){
   cout << "The current number is " << i << ".\n";
}
```

This will print:

```
The current number is 0.
The current number is 1.
The current number is 2.
The current number is 3.
The current number is 4.
The current number is 5.
The current number is 6.
The current number is 7.
The current number is 8.
The current number is 9.
```

Notice how 10 doesn't print, because we told the loop to stop as soon when `i` was no longer less than 10. The first time the loop executes, `i` equals 0, so the loop prints out the message "The current number is 0." and then adds one to `i`, making `i` 1. Then the loop executes again, and we print "The current number is 1." Then `i` is increased by 1 again, making it 2, etc.

We can also modify the loop so that the loop variable changes in different ways---just by changing the initialization and the modification pieces. Say we want to count backwards from 4 to 1. We can create the loop like this:

```cpp
for (int i=4; i>=1; i--){
   cout << "The current number is " << i << ".\n";
}
```

Here, we begin with `i` set to 4. We loop while `i > = 1`. We tell the computer to subtract one from `i` each time the loop runs with `i--`. This loop prints:
```cpp
The current number is 4.
The current number is 3.
The current number is 2.
The current number is 1.
```
We can also count by numbers other than one and negative one. Let's say we only want to print out odd numbers. We could change the loop to count by 2s from 1 to 7 in the following way:
```cpp
for (int i=1; i<9; i+=2){
   cout << "The current number is " << i << ".\n";
}
```
With this loop initialization, we get the following output:
```cpp
The current number is 1.
The current number is 3.
The current number is 5.
The current number is 7.
```
The loop begins with `i=1` and increases by 2 every time. Notice that it stops before reaching 9. To make more complicated loops, all you have to do is think carefully about the loop counter. Where do you want it to start? Where should it stop? How do you want to count?

### Exercise 3.6.1:

- Write a loop that prints every third number starting at 15 and going down to 6 (so 6 is included in the loop).

{% include callout_red_cup.html task="[Exercise 3.6.1]" %}

Woot, woot! Making progress. :)

## Nested Loops

You can also nest loops inside one another. Let's say we want to do a simple summation program. Imagine we want to sum each number from 1 to 4 with each number from 1 to 4. So, we essentially want to do this:

```
num1	+	num2	=	Sum
1	+	1	=	2
1	+	2	=	3
1	+	3	=	4
1	+	4	=	5
2	+	1	=	3
2	+	2	=	4
2	+	3	=	5
2	+	4	=	6
```

At the end, we will have 16 sums (4x4).

In code, we can find these sums using two for loops, one nested inside the other. Let's think of `num1` as the value of one loop and `num2` as the value of the other loop. We know from the examples above how to generate a loop that generates the numbers from 1 to 4, so we will do this for num1:

```cpp
for (int num1=1; num1<5; num1++){
   //put code here
}
```

We know that for each value of `num1`, we want to sum it with all values of `num2`, which are the numbers 1 to 4. So we can use another for loop to generate those numbers. Since we want to generate all the values of `num2` for each value of `num1`, let's put the `num2` for loop inside of the `num1` for loop, like this:

```cpp
for (int num1=1; num1<5; num1++){  // num1 for-loop
   for (int num2=1; num2<5; num2++){  //num2 for-loop
      cout << num1 << " + " << num2 << " = " << num1+num2 << "\n";  //prints out num1+num2
   }
}
```

And this gives us the output:

```
1 + 1 = 2
1 + 2 = 3
1 + 3 = 4
1 + 4 = 5
2 + 1 = 3
2 + 2 = 4
2 + 3 = 5
2 + 4 = 6
3 + 1 = 4
3 + 2 = 5
3 + 3 = 6
3 + 4 = 7
4 + 1 = 5
4 + 2 = 6
4 + 3 = 7
4 + 4 = 8
```

Notice that the first number that prints out is the `num1` variable, and the second number is the `num2` variable, and the final number is the sum of `num1` and `num2`. Let's quickly talk through the loop. We begin with `num1` being equal to 1 and `num2` being equal to 1, and `num1+num2` equaling 2. Then the `num2` loop advances by 1, because the inner loop has to finish before the outer loop can advance. So `num1` is 1 and `num2` is 2 and their sum is 3. Then `num2` advances by 1 again, and `num1` is 1 and `num2` is 3 and their sum is 3. Finally, `num1` is 1 and `num2` is 4 and their sum is 5. The next time `num2` is incremented it becomes 5, violating the less than 5 condition of the loop, and so the `num2` loop finishes. Now the `num1` loop advances by 1, so `num1` is 2. Now the `num2` loop starts all over again from the beginning, and `num2` is 1 and `num1+num2` is 3, and so forth and so on. Nested loops can be a little tricky, so if they are confusing, ask for help!

### Exercise 3.6.2:

- Write a program that multiplies all the odd numbers between 1 and 9 by all the even numbers between 2 and 10. Hint: follow the example above, but don't forget to change your loop initializations.

Good work!

{% include callout_red_cup.html task="[Exercise 3.6.2]" %}

## While Loops

We typically use while loops when we don't know how many times the loop should execute. For example, let's say you are trying to get input from a user that is a number between 1 and 10. while the user keeps typing in numbers that are too large or too small, you can ask her for new input until she enters a number between 1 and 10. Here's what this while loop would look like:

```cpp
int main(){
   int userInput;

   //get input from user
   cout << "Enter a number between 1 and 10: ";
   cin >> userInput;

   //as long as userInput is less than 1 or greater than 10
   while((userInput < 1) || (userInput > 10)){
      cout << "Read directions!  Enter a number between 1 and 10: ";
      cin >> userInput;  //get new input from the user
   }
   //when we reach this line, we know the user entered a number between 1 and 10,
   //or else we would still be stuck in the while loop.
   cout << "You entered " << userInput << ".\n";
}
```

You'll notice that the logical expressions appear again—this time in the parentheses after the while. Once again, the loop will continue as long as this expression is true.

Let's walk through what is happening in this program.

We first get some input from the user.

We begin the while loop by checking the input to see if it is less than 1 or greater than 10.

If it is, we yell at the user and ask for new input, and we make sure to save the new input to `userInput`. (Why is this so important? We'll see in a bit.)

Then the program loops back to the beginning of the while loop and checks to see if `userInput` is less than 1 or greater than 10.

If it still is, we execute the loop again and ask for new input.

We continue this as many times as necessary until the user cooperates.

As soon as the user enters a number between 1 and 10, we break out of the while loop, because we only execute the while loop if `userInput` is less than 1 or greater than 10.

We then print out the number.

In the above program, we made sure to save the new user input to the same variable as the old user input. This step is important because that's the variable being evaluated in the logical expression—if we didn't update it, the while loop would never stop! To illustrate this, let's change the above while loop to make it incorrect by introducing another variable called `newUserInput`:

```cpp
while((userInput < 1) || (userInput > 10)){
   cout << "Read directions!  Enter a number between 1 and 10: ";
   cin >> newUserInput;  //get new input from the user and save it to new variable
}
```

This loop begins by checking to see if `userInput` is less than 1 or greater than 10. Let's say that `userInput` equals 100, so the loop will run.

Inside the loop, the program prints out a nasty message to the user and gets new input from the user, the number 5. This time, however, 5 is saved to a different variable called `newUserInput`.

Then the program checks the loop condition again. Since we never changed the value in `userInput`, it still equals 100, so the loop will run again even though the user just entered a valid number.

In fact, this loop will run forever! This is called an infinite loop. To avoid this, always make sure that you update the loop variable somehow by changing its value so that eventually your loop will stop.

{{ site.data.alerts.tip }}
If your program ends up in an infinite loop, you need to know how to terminate it. Go into your terminal and type Ctrl-C to terminate it if this happens.
{{ site.data.alerts.end }}

### Exercise 3.6.3:

- Create a program that asks the user to enter a number between 5 and 50. If the user enters invalid input, print out a message to the user asking them to try again and keep getting input from the user until they enter a valid number.

- Bonus: Can you keep track of the number of attempts a user makes to enter a number, and then print it out when they finally enter a valid number?

{% include callout_red_cup.html task="[Exercise 3.6.3]" %}

## Next Step

Proceed to ["Arrays"](arrays.html)
