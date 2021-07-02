---
title: "Functions"
tags: [c++]
keywords: c++
sidebar: tutorials
permalink: functions.html
---

A <b>function</b> is a group of instructions. Often, functions are used to organize code by breaking long programs into shorter functions that together make up the composition of the longer program.

We might have a `getLetter` function that asks the user for a lowercase letter, or an `averageNumbers` function that averages a list of numbers.

Functions allow code to be modular --- write a function once, and use that function many times.

## Defining a Function

Recall the function `main()`

```cpp
int main(){
     //code goes here
}
```

We begin by declaring the <b>return type</b> of main to be an integer. This tells the computer that we intend for main to send back an integer when it is finished.

Usually, this is accomplished through a <b>return statement</b>.

`main()` generally returns a 1 if there was an error and 0 if the program completes successfully.

We'll talk more about return types soon.

We then write the name of the function, main, and follow it with a set of parentheses.

These parentheses are for <b>parameters</b>. Parameters are things like numbers or variables that are sent into a function so that it can use them in its code.

For our purposes, they are empty for main, but we'll see them in action in other functions soon.

Finally we have a code block inside curly braces.

## Exercise 3.3.1: Example Function

{% include note.html content="We're taking off the training wheels. Organize your code yourself now into directories that you create. Try to keep on top of being organized. Be prepared to demo everything to camp staff to verify your progress." %}

Let's try writing a very simple function that prints the greeting "Hello World!". We will <b>call</b> (run) this function from main. It won't take any parameters or return anything, so the return type of this function will be <b>void</b>, the return type for a function which returns nothing. Here's how we would set it up:

```cpp
#include <iostream>
using namespace std;

void printGreeting(){
   cout << "Hello World!\n";
}

int main(){
   printGreeting();
}
```

Here, we made the printGreeting function exactly like we made main. We declared its `return` type to be void, named it `printGreeting`, and put no parameters inside the parentheses. Inside the curly braces, we wrote the same code we used for our very first C++ program.

What's interesting is how we call, or run, the function. Inside of main, we call the function by naming it and then following it by a set of empty parentheses, which we'll explain in a minute. As always, we end the line with a semi-colon.

The way that this program works is the following: the computer begins running the program inside the main function. When it gets to the `printGreeting` function, it "jumps" to where we defined the `printGreeting` function and starts executing that code. When it gets to the end of the `printGreeting` function, it jumps back to the `main` function exactly where it left off and continues executing the rest of the code in main.

- Type in the code above and see that it executes.

### Exercise 3.3.2:

- Modify the program so that main calls `printGreeting()` twice. How does the output change?

## Parameters

Parameters allow you <b>pass</b> values to a function.

We're going to change `printGreeting` so that it prints out "Hello, \<name\>", where name is some name that the user enters.

`printGreeting` will be passed the name to print out from `main`.

The general layout of this program will be:

1. Start in `main`

2. Get a name from the user

3. Send that name to `printGreeting`

4. Print out the hello message, return to `main`

{{ site.data.alerts.tip }}
We know that this sounds complicated, but we you'll master it.
{{ site.data.alerts.end }}

When a function takes a parameter, we tell the function the type of the parameter, as well as give it a name, much like a variable.

For `printGreeting` the parameter will be a `string`. We will call it `name`.

{{ site.data.alerts.tip }}
`name` is <b>scoped</b> to `printGreeting`. It can be referred to and used like a variable, but only inside this function.
{{ site.data.alerts.end }}

{{ site.data.alerts.tip }}
Scoping applies to variables, too. If you declare a variable inside `printGreeting`, you cannot use it outside of `printGreeting`.
{{ site.data.alerts.end }}

```cpp
void printGreeting(string name){
   cout << "Hello " << name << "!" << endl;
}
```

Anything that calls the `printGreeting` function needs to provide a `string` value that will be called name inside the function.

We will to get input from the user and provide that input when we call the `printGreeting` function from main:

```cpp
int main(){
   string userName;
   cout << "Enter a name: ";
   cin >> userName;
   printGreeting(userName);
}
```

Here, we got a `string userName` from the user and sent it to the `printGreeting` function by placing it inside the parentheses.

Before going further, we need to discuss the difference between arguments and parameters. The value that is placed in the parentheses is called the <b>argument</b> to the function. (Or, if there are more than one, they are the arguments) Arguments differ from parameters in that arguments are what you send to a function and parameters are what a function expects to receive.

When the `printGreeting` function is called from `main`, the argument `userName`'s value is copied to the parameter `name` in `printGreeting`. While the computer is executing the code in `printGreeting`, it can't use the variable `userName`, because that variable is only defined (available) in main (due to scoping). So that's why we have a parameter name—the value of `userName` gets copied to `name` so that the program has access to that data. When the computer finishes executing `printGreeting` and returns to `main`, it can again use the variable `userName`, but it can no longer use `name`. This is again a case of scoping, which is where the variable is defined and can be used.

As we mentioned before, on of the reasons that functions are so great is that we can reuse them and give them different arguments. For example, without changing the `printGreeting` function at all, we can use it to print greetings to three different people:

```cpp
#include <iostream>
using namespace std;

void printGreeting(string name){
   cout << "Hello " << name << "!\n";
}


int main(){
   printGreeting("Alison");
   printGreeting("Brian");
   printGreeting("Clifford the Big Red Dog");
}
```

And we would get the following output:

```cpp
Hello Alison!
Hello Brian!
Hello Clifford the Big Red Dog!
That's pretty convenient.
```

### Exercise 3.3.3:
Using the code above as a base, add two calls to printGreeting() in main so that both of you are also greeted.

Now that you've been greeted...

{% include callout_red_cup.html task="[Exercise 3.3.1, Exercise 3.3.2, Exercise 3.3.3]" %}

## Returning Results

We can also use functions to do computation for us and return the answers back to `main` (or to other functions).

For example, let's imagine that we want to write a function called squareANum that calculates the square of a number. We know from math class that the square of a number is that number multiplied by itself. So, let's write a function that takes a floating point number and squares it. After we figure out the square of the number (which we'll call numSquared), we'll need a way to return our answer back to the function that called it.

To do this, we say:

```cpp
return numSquared;
```

This is called the <b>return statement</b>, and it is always the last line executed in a function.

Since we know that we are squaring floats, we will be returning a float, so the return type of this function will be a float as well.

Now we're ready to write our function:

```cpp
float squareANum(float num){
   float numSquared;

   numSquared = num * num;
   return numSquared;
}
```

We write the function as we normally would, and then tell the computer to `return numSquared` to the function that called it.

Since we are returning something to `main`, we need to set up a variable to store the value that we are returning.

This part of programming is like playing a game of catch. You can imagine that `squareANum` and main are playing a game of catch, and `squareANum` is throwing a ball named `numSquared` at main. If main doesn't catch the ball, the ball will fall in the grass and be lost. In programming, main catches the ball by having a variable in place to store the return value---if it doesn't, the value is gone forever. Since we want to store the result, we'll set our call to `squareANum` in `main` equal to the variable result. Here's the whole program:

```cpp
#include <iostream>
using namespace std;

float squareANum(float num){
   float numSquared;

   numSquared = num * num;
   return numSquared;
}

int main(){
   float numToSquare, theSquaredNumber;

   numToSquare = 5.5;
   theSquaredNumber = squareANum(numToSquare);  //catch the returned value
   cout << numToSquare << " squared equals " << theSquaredNumber << endl;
}
```

Note that you must either:

1. Write a function's code earlier in the program text than it is called or

2. Include a <b>prototype</b> of that function at the top of the file.

A <b>function prototype</b> is the return type, name, and parameter followed by a semicolon. For instance, the prototype for `squareANum` would be:

`float squareANum(float num);`

Function prototypes usually appear before the first function and after the include files.

### Exercise 3.3.4:

- Write a program similar to the one above that triples a number and adds 5 to it.

## Multiple Parameters

We can also write functions that take multiple parameters---and those parameters can even have different types.

For example, we can modify the `printGreeting` function so that it takes both a `string` `name` and an integer `age`, and prints out a message about that person's age:

```cpp
#include <iostream>
#include <string>

using namespace std;

void printGreeting(string name, int age){
   cout << "Hello " << name << "." << endl;
   cout << "You are " << age << " years old." << endl;
}


int main(){
   printGreeting("Ronald McDonald", 49);
}
```

We just have to remember to send the function all parameters it expects as arguments when we call it. Although we can have different numbers and types of parameters, a function can only return one value, so think carefully about what result you want from a function before you write it.

### Exercise 3.3.5

- Modify the `printGreeting` function to also take a `string birthdayMonth` parameter, and print out a message that tells them how old they will be the next time it is that month. For the Ronald McDonald example, the output might be, "You will be 50 next January".

{% include callout_red_cup.html task="[Exercise 3.3.4, Exercise 3.3.5]" %}

You've done a great a job learning about functions.

Now, let's learn about a special data representation, the [object](objects.html).

## Next Step

Proceed to ["Classes and Objects"](objects.html).
