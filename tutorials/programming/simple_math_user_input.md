---
title: "Simple Math and User Input"
tags: [c++]
keywords: c++
sidebar: tutorials
permalink: simple_math_user_input.html
---

Let's look at an example C++ program. This program will ask the user their weight on Earth, store that information, convert that weight to their weight on the moon, and then print their moon weight.

An object that weighs 1.0 pounds on Earth would weigh 0.1654 pounds on the moon.

In C++, multiplication is represented with the * symbol.

The program will save all the numbers it needs in <b>variables</b>. A variable stores a number or a mathematical formula.

For example:

```cpp
x = 4;
y = 5 * x;
```

{{ site.data.alerts.tip }}
Unlike in mathematical formulas, the `=` sign means <b>assignment</b>. It sets the value of the variable, but does not state that those two things are equal.

So in this short program:
<br>
<br>
y = 0;
<br>
x = y;
<br>
y = 5;
<br>
<br>

At the end, `x` has `0` in it, NOT 5.
{{ site.data.alerts.end }}

{{ site.data.alerts.tip }}
A good variable name describes the value that it stands for. When naming variables, use better names than x and y. 
{{ site.data.alerts.end }}

{{ site.data.alerts.tip }}
Variables names cannot have spaces in them and cannot start with numbers.
{{ site.data.alerts.end }}

## Types

C++ requires types for variables.

For example, a variable storing a number with a decimal should be a float, which stands for floating (decimal) point number.

Variables must be declared before they are used. Generally this is done by saying the variable type and then the names of all the variables that are that type at the first line of the function.

Here's a quick reference of types in C++:

Type    | Example
--------|-------------
float	| 0.124 or 4.0
int	    | 4 or 134
string	| "Hello World"
bool	| true/false

Let's write an algorithm for this program.

1. Save the conversion factor (0.1654) as the variable `conversionFactor`

2. Ask the user's weight

3. Save the weight to a variable called `earthWeight`

4. Multiply earthWeight and conversionFactor and save the result as the variable `moonWeight`

5. Display `moonWeight` to the user

## Getting User Input

This program will require input from the user. To get that input, use `cin`.

`cin` takes whatever the user types and assigns it to a variable. The <b>syntax</b> (the structure) of the command looks like this:

```cpp
cin >> myVariable;
```

{{ site.data.alerts.tip }}
Note the similarity to `cout`.
{{ site.data.alerts.end }}

When the computer reaches `cin` in the program, it will display a prompt for the user to type. The user can then type and hit the Enter key, and the computer saves whatever the user typed to the variable called myVariable.

## Printing a Variable

To print out the person's weight on the moon, use a second `<<`, just like before `endl` in the previous tutorial.

```
cout << "Something weighing" << earthWeight << "lbs on earth would would weigh "<< moonWeight << " lbs on the moon." << endl;
```

This sends the whole sequence of things to cout to be displayed.

## Exercise 3.2.1: Full Program

{% include note.html content="Any text preceded by `//` is a comment.
<br>Comments are ignored by the compiler and are used by programmers to explain parts of their code." %}


{{ site.data.alerts.tip }}
It's good practice to have short comments in your code, so you can remember what it does later.
{{ site.data.alerts.end }}

```cpp
#include <iostream>
using namespace std;

int main(){
  float conversionFactor, earthWeight, moonWeight;  //define variables as floats

  //Prompt the user to enter weight
  //Note that there is no "endl", so the prompt will appear on the same line.
  cout << "Enter your weight on earth:";
  cin >> earthWeight; //Store what the user types as earthWeight
  conversionFactor = 0.1654;
  moonWeight = earthWeight*conversionFactor;
  cout << "Something weighing" << earthWeight << "lbs on earth would would weigh "<< moonWeight << " lbs on the moon." << endl;  //print out conversion
}
```

## Operators

Some common math operators in C++:

Operator |	Operation
:-------:|:---------
+	     | addition
−	     | subtraction
*	     | multiplication
/	     | division
%	     | modulus (remainder)

When you divide two integers, the remainder of the two numbers is left out. This is called <b>truncation</b>.

In integer division., `5 / 2` will give you 2, not 2.5. If you want the full value, you must use floats.

The `%` (<b>modulus</b>) operator gives you the remainder of integer division.

So if you want the remainder of `5 / 2` (which is 1), you would say:

```cpp
int rem;
rem = 5%2;
```

This is very useful in programming, since you can easily decide if a number is even, odd, or a multiple of some other number.

## Exercise 3.2.2:

Write a program that takes a weight on the moon and converts it to Earth weight.

{{ site.data.alerts.tip }}
What's the mathematical opposite of multiplication?
{{ site.data.alerts.end }}

## Exercise 3.2.3:

Write a program that asks the user for two numbers, and then prints out the sum of the two numbers. Hint: Use multiple cin commands.

{% include callout_red_cup.html task="[Exercise 3.2.1, Exercise 3.2.2, Exercise 3.2.3]" %}

{% include note.html content="Campers should demonstrate the output of Exercise 3.2.1, Exercise 3.2.2, Exercise 3.2.3, and show their code to camp staff." %}

## Next Step

Proceed to ["Functions"](functions.html).
