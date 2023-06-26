# Arrays

Arrays allow us to store a list of values of one type in a single variable.

For example, if you wanted to store a list of 10 integers in the same list or variable, you would make an array like this:

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

int main() {
    int arr[3]; // create an array that can store 3 integers
    arr[0] = 1;
    arr[1] = 2;
    arr[2] = 3;
```
{{ site.data.alerts.end }}

Let's take a look at `int arr[3]`. The overall structure of defining an array in C++ is:

* `int`: Write the type of data this array is going to store (int, float, double, etc.).
* `arr`: Write the name of this array variable.
* `[3]`: Inside square brackets [], specify how many items this array can store (called the **length** of the array).


Another important thing to notice is array indexing. When we make `arr` above, it has 3 slots. We started to assign values to `arr` beginning from slot 0. This is because arrays follow 0-based indexing. Simply put, this means that the location of the first element is 0, not 1. More generally, to access any index or slot in an array, you should do something like this:

```
cout << array[i] << endl; // this will print the value at the i^th slot of array

```


## Arrays and Loops

Arrays can also be initialized using `for` loops. Loops execute the same code multiple times.

This is how you should initialize any big array programmatically:

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

int main() {
    int arr[10];
    for (int i = 0; i < 10; i++) {
        // this array stores integers 1 - 10
        arr[i] = i + 1;
    }
```
{{ site.data.alerts.end }}

Let's take a look at the syntax of `for` loops: `for (int i = 0; i < 10; i++) {`
* `for (`: This is the starting syntax for a `for` loop. 
* `int i = 0; `: We create a variable called `i` to count how many times our loop has executed. Let's start at 0, because that's the first index of an array. NOTE THE SEMICOLON!!!
* ` i < 10; `: This is the condition—this loop will run as long as our counter, `i`, is less than 10. Since we're starting at 0, this loop will run exactly 10 times. NOTE THE SEMICOLON!!!
* `i++`: We increase our counter, `i`, by 1 each time the loop executes.
* `) {`: Make sure you close the parentheses and include an opening curly brace for the code you will put in the loop!

Since our counter goes from 0 to 10, we can also use `i` to access the indices (index plural), or locations, of the array. `arr[i] = i + 1;`

{{site.data.alerts.note}}
PLEASE ASK QUESTIONS about loops! High school CS classes typically spend up to a month learning about loops, but y'all are doing it in only one day! Kudos to you!
{{site.data.alerts.end}}


### Exercise 3.6.1:

- Create an array that stores 10 integers. Then, print the average of all 10 of those numbers. Hint: loop through each index of the array using a `for` loop.

{{+}}Tutorial 3.6.1, 3_6_1{{+}}


### Exercise 3.6.2:

- Write a program that asks a user to enter 5 numbers, puts those numbers in an array, and then prints out the numbers in the array backwards. Hint: use a loop that counts backwards, with a decreasing counter.

{{+}}Tutorial 3.6.2, 3_6_2{{+}}

{{-}}Classes and Objects, in_person/programming_objects.md, Next{{-}}
