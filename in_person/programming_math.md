# Math and User Input

In C++, multiplication is represented with the * symbol.

C++ stores values in **variables**.

For example:

{{ site.data.alerts.callout_code_div }}
```
x = 4;
y = 5 * x;
```
{{ site.data.alerts.end }}

{{ site.data.alerts.tip }}
Unlike in mathematical formulas, the `=` sign means **assignment**. It sets the value of the variable, but does not state that those two things are equal.

So in this short program:

```cpp
y = 0;
x = y;
y = 5;
```

At the end, x has 0 in it, not 5!
{{ site.data.alerts.end }}

{{ site.data.alerts.tip }}
A good variable name describes the value that it stands for. When naming variables, use better names than x and y. 
{{ site.data.alerts.end }}

{{ site.data.alerts.tip }}
Variable names cannot have spaces in them and cannot start with numbers.
{{ site.data.alerts.end }}

## Types

C++ requires types for variables.

A variable storing a number with a decimal should be a `float`, which stands for floating (decimal) point number.

Variables must be declared before they are used. This is done by saying the variable **type** and then the name the variable.

Here's a quick reference.

Type    | Example
--------|-------------
float	| 0.124 or 4.0
int	    | 4 or -134
string	| "Hello World"
bool	| true/false

An object that weighs 1.0 pounds on Earth would weigh 0.1654 pounds on the moon. You will now write a short computer program which converts Earth weight to Moon weight.

1. Save the conversion factor (0.1654) as the variable `conversionFactor`

2. Ask the user's weight

3. Save the weight to a variable called `earthWeight`

4. Multiply `earthWeight` and `conversionFactor` and save the result as the variable `moonWeight`

5. Display `moonWeight` to the user

## Getting User Input

This program will require input from the user. To get that input, use `cin`.

`cin` takes whatever the user types and assigns it to a variable. The **syntax** (the structure) of the command looks like this:

```cpp
cin >> myVariable;
```

{{ site.data.alerts.tip }}
Note the similarity to `cout`.
{{ site.data.alerts.end }}

When the computer reaches `cin` in the program, it will display a prompt for the user to type. The user can then type and hit the Enter key, and the computer saves whatever the user typed to the variable called `myVariable`.

## Printing a Variable

To print out the person's weight on the moon, use a second `<<`, just like before `endl` in the previous tutorial.

```
cout << "Something weighing " << earthWeight << "lbs on earth would weigh "<< moonWeight << " lbs on the moon." << endl;
```

This sends the whole sequence of things to cout to be displayed.

### Tutorial 3.2.1: Full Program

{{ site.data.alerts.note }}
Any text preceded by `//` is a comment.
Comments are ignored by the compiler and are used by programmers to explain parts of their code.
{{ site.data.alerts.end }}

{{ site.data.alerts.tip }}
It's good practice to have short comments in your code, so you can remember what it does later.
{{ site.data.alerts.end }}

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

int main(){
  float conversionFactor, earthWeight, moonWeight;  //define variables as floats

  //Prompt the user to enter weight
  //Note that there is no "endl", so the prompt will appear on the same line.
  cout << "Enter your weight on earth: ";
  cin >> earthWeight; //Store what the user types as earthWeight
  conversionFactor = 0.1654;
  moonWeight = earthWeight*conversionFactor;
  //print out conversion
  cout << "Something weighing " << earthWeight << "lbs on earth would weigh "<< moonWeight << " lbs on the moon." << endl;  
  return 0;
}
```
{{ site.data.alerts.end }}

{{ site.data.alerts.tip }}
Notice how the value for earthWeight is printed with "lbs" right next to it? Cout will not add spaces between the strings and the variables you print. For readability, it's good practice to include these spaces yourself.
{{ site.data.alerts.end }}


## Operators

Some common math operators in C++:

Operator |	Operation
:-------:|:---------
+	     | addition
−	     | subtraction
*	     | multiplication
/	     | division
%	     | modulus (remainder)

When you divide two integers, the remainder of the two numbers is left out. This is called **truncation**.

In integer division, `5 / 2` will give you 2, not 2.5. If you want the full value, you must a float.

The `%` (**modulus**) operator gives you the remainder of integer division.

So if you want the remainder of `5 / 2` (which is 1), you would say:

{{ site.data.alerts.callout_code_div }}
```
int rem;
rem = 5%2;
```
{{ site.data.alerts.end }}

{{ site.data.alerts.note }}
In programming there is a difference between variable defintition and assignment. The first line in the above code block is an example of variable definition because a variable of type `int` named rem was declared. The second line is an example of variable assignment because the variable was given the value of 5%2.
{{ site.data.alerts.end }}

This is very useful in programming, since you can easily decide if a number is even, odd, or a multiple of some other number.

### Exercise 3.2.1:
Copy the code above (Tutorial 3.2.1) into a new file named ex_3_2_1.cpp in the directory named 3_2. Then compile and run this program to ensure it is working properly.

{{+}}Exercise 3.2.1, 3_2_1{{+}}

### Exercise 3.2.2:

Write a new program that takes a weight on the moon and converts it to Earth weight.

{{ site.data.alerts.tip }}
What's the mathematical opposite of multiplication?
{{ site.data.alerts.end }}

{{+}}Tutorial 3.2.2, 3_2_2{{+}}

### Exercise 3.2.3:

Write a new program that asks the user for two numbers, and then prints out the sum of the two numbers. Hint: Use multiple cin commands.

{{+}}Tutorial 3.2.3, 3_2_3{{+}}

{{-}}Functions, in_person/programming_functions.md, Next{{-}}