# Functions

A **function**: a short program that is used as part of a larger program. It is a set of instructions with a common goal, working together to find a value. It is enclosed by curly braces {}.

## Defining a Function

Look at `main()`

{{ site.data.alerts.callout_code_div }}
```
int main(){
     // code goes here
     return 0;
}
```
{{ site.data.alerts.end }}

{{ site.data.alerts.note }}
Just like variables, functions also have a type! The main difference is that a variable stores a value, whereas a function finds a value and then returns it. 
The type of value that a function returns is called its **return type**.
{{ site.data.alerts.end }}

`main()`'s return type is `int` (it says so to the left of `main`). `return 0;` gives a value (0) back to the thing that called the function.

When `main()` is done running, it gives back an int to Linux.

{{ site.data.alerts.note }}

`main()` should always return 0, because this tells Linux that the program ran successfully.
{{ site.data.alerts.end }}

### Tutorial 3.3.1: Example Function

Let's write a "Hello World!" function.

We will **call** (run) this function from `main()`.

A function that does not return anything has a **return type** of **void**. This function does not return anything because it only prints something, and printing is not finding a value to return.

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

void printGreeting(){
   cout << "Hello World!" << endl;
}

int main(){
   printGreeting();
   return 0;
}
```
{{ site.data.alerts.end }}

This function works like the first **Hello World!** program, but the printing happens in a function.

```cpp
printGreeting();
```

This line **calls* the function, running the code inside of it.

Here's how the program works:
1. The computer begins running the program inside the `main` function.
2. When it gets to `printGreeting()` function, it **calls** and **executes** `printGreeting()`.
3. When it gets to the end of the `printGreeting` function, `printGreeting` **returns** back to the `main` function where it left off.
4. It continues executing the rest of the code in `main`.

### Exercise 3.3.1: Example Function
Copy the code above and see that it executes.

{{+}}Tutorial 3.3.1, 3_3_1{{+}}

### Exercise 3.3.2:
Modify the program so that `main` calls `printGreeting()` twice.

{{+}}Tutorial 3.3.2, 3_3_2{{+}}

## Parameters

Parameters allow you **pass values** to a function. We need to **pass in** parameters if one function needs more information from another function in order to execute.

We're going to change `printGreeting` so that it prints out "Hello, {name}", where name is a name that the user enters.

`printGreeting` will be passed the name to print out from `main`.

The general layout of this program will be:

1. Start in `main`.
2. Get a name from the user.
3. Send that name to `printGreeting`.
4. Print out the hello message, then return to `main`.



{{ site.data.alerts.callout_code_div }}
```
void printGreeting(string name){
   cout << "Hello " << name << "!" << endl;
}
```
{{ site.data.alerts.end }}

`printGreeting` takes a parameter called `name` of type `string`.

{{ site.data.alerts.callout_code_div }}
```
int main(){
   string userName;
   cout << "Enter a name: ";
   cin >> userName;
   printGreeting(userName);
   return 0;
}
```
{{ site.data.alerts.end }}

Here, we get a value for `string userName` from the user and send it to the `printGreeting` function by placing it inside the parentheses.

## Scoping 

In the example, the parameter `name` is **scoped** to `printGreeting`. It can be used like a variable, but only inside `printGreeting`.

Similarly, if you declare a variable inside `printGreeting`, you cannot use it outside of `printGreeting`.

{{ site.data.alerts.callout_code_div }}
```
void printGreeting(string name){
   string myName = "Bob";
   cout << "Hello " << name << "! My name is " << myName << "." << endl;
}

int main(){
   printGreeting("Hannah");
   cout << "Hello " << myName << "!" <<endl;
}
```
{{ site.data.alerts.end }}

This code won't work. `myName` is scoped to `printGreeting`. `main` cannot access that variable.

### Arguments vs Parameters

In the program above `string name` is a **parameter**.
`"Hannah"` is an **argument**, or the actual value of the parameter.

The **parameter** states the information the function needs.

The **argument** is the information.

{{ site.data.alerts.callout_code_div }}
```
void printGreeting(string name){
   cout << "Hello " << name << "!" << endl;
}

int main(){
   string userName ="Hannah";
   printGreeting(userName);
}
```
{{ site.data.alerts.end }}

During the execution of this code, the variable `userName` is copied to the **parameter** `name` in `printGreeting`.

While the computer is executing the code in `printGreeting`, it can't use the variable `userName`. This is because `userName` is only available in `main` (due to **scoping**). 

This is why we have the parameter `name` - the value of `userName` gets passed in as the parameter `name` so that `printGreeting` has access to that data. 

When the computer finishes executing `printGreeting` and returns to `main`, it can once again use the variable `userName`. 

{{ site.data.alerts.tip }}
Code blocks are a great way to keep track of scoping! Any variables that are declared inside of a block (enclosed by `{}`) can only be used inside of that block.
{{ site.data.alerts.end }}

Functions are great because they can be called with different arguments being passed into the same parameters.

To illustrate this, without changing `printGreeting`, we can use it to print greetings to three different people:

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

void printGreeting(string name){
   cout << "Hello " << name << "!" << endl;
}


int main(){
   printGreeting("Peter");
   printGreeting("Justin");
   printGreeting("Joydeep");
   return 0;
}
```
{{ site.data.alerts.end }}

This gives us the following output:

{{ site.data.alerts.callout_code_div }}
```
Hello Peter!
Hello Justin!
Hello Joydeep!
```
{{ site.data.alerts.end }}

### Exercise 3.3.3:
Edit the code above to add a call to printGreeting() in `main` so that you are also greeted.

{{+}}Tutorial 3.3.3, 3_3_3{{+}}

## Returning Results

So far, we've only discussed functions that have a return type of **void**, which is a return type that doesn't return any values. We can also use functions to do computations for us and return the answer(s) back to `main` (or to other functions).

For example, let's imagine that we want to write a function called `squareANum` that calculates the square of a number. We know from math class that the square of a number is that number multiplied by itself. So, let's write a function that takes a floating point number and squares it. After we figure out the square of the number (which we'll call `numSquared`), we'll need a way to return our answer back to the function that called it.

To return a value, we say:

```cpp
return numSquared;
```

This is called the **return statement**, and it is *always* the last line executed in a function. This is because we are *returning* to wherever we were in the code when the function was called.

{{ site.data.alerts.note }}
This means that any code after the return statement in a function will not be executed!
{{ site.data.alerts.end }}

Now we're ready to write our function:

{{ site.data.alerts.callout_code_div }}
```
float squareANum(float num){
   float numSquared;

   numSquared = num * num;
   return numSquared;
}
```
{{ site.data.alerts.end }}

Notice that since we're returning a float value, we have the return type as `float` instead of `void`, and then tell the computer to `return numSquared` to the function that called it.

Since we are returning something to `main`, we need to set up a variable in `main` to store the value that is received from `squareANum`. Let's call this variable `theSquareNumber`.

In other words, we need to create a variable in `main` to store the value that is returned from `squareANum`. Here's the whole program:

{{ site.data.alerts.callout_code_div }}
```
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
   theSquaredNumber = squareANum(numToSquare);  // catch the returned value by storing it in a variable
   cout << numToSquare << " squared equals " << theSquaredNumber << endl;
   return 0;
}
```
{{ site.data.alerts.end }}

Note that in order to call a function, you must write the function's code earlier in the program text than it is called.


### Exercise 3.3.4:

- Write a new program similar to the one above that triples a number and adds 5 to it.

{{+}}Tutorial 3.3.4, 3_3_4{{+}}

## Multiple Parameters

We can also write functions that take multiple parameters---and those parameters can even have different types!

For example, we can modify the `printGreeting` function so that it takes both a `string name` and an `int age`, and prints out a message about that person's age:

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
#include <string>

using namespace std;

void printGreeting(string name, int age){
   cout << "Hello " << name << "." << endl;
   cout << "You are " << age << " years old." << endl;
}


int main(){
   printGreeting("Ronald McDonald", 49);
   return 0;
}
```
{{ site.data.alerts.end }}

We just have to remember to send the function **all parameters** it expects as arguments when we call it, in the **exact order** they are listed. Although we can have different numbers and types of parameters, a function can only return one value, so think carefully about what result you want from a function before you write it.

### Exercise 3.3.5

- Modify the `printGreeting` function to also take a `string birthdayMonth` parameter, and print out a message that tells them how old they will be the next time it is that month. For the Ronald McDonald example, the output might be:

{{ site.data.alerts.callout_code_div }}
```
Hello Ronald McDonald.
You are 49 years old.
You will be 50 next January.
```
{{ site.data.alerts.end }}

{{+}}Tutorial 3.3.5, 3_3_5{{+}}

{{-}}If and Switch, in_person/programming_decisions.md, Next{{-}}

