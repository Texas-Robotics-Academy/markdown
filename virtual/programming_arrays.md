# Arrays - Online

Arrays allow us to store a list of values of one type in a single variable.

For example, if you wanted to store a list of 10 integers in the same list or variable, you would make an array like this:

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

int main() {
    int arr[3]; // create an array that stores 3 integer types values
    arr[0] = 1;
    arr[1] = 2;
    arr[2] = 3;
```
{{ site.data.alerts.end }}

The overall structure of defining an array in C++ is:

Write the type of data this array is going to store (int, float, double etc.)
Then write the name of this array variable
Finally, open and close square brackets, and inside the square brackets specify how many items this array can store (called the **length** of the array)

Another important thing to notice is array indexing. When we make `arr` above, it has 3 slots. We started to assign values to `arr` beginning from slot 0. This is because arrays follow 0-based indexing. Simply put, this means that to access the index of the first element in any array is 0, not 1. And more generally, to access any index or slot in an array, you should do something like this:

```
cout << array[i] << endl; // this will print the value at the i^th slot of array
```

### Exercise 3.6.1:

- Create an array that stores 10 numbers. Then, print the average of all 10 of those numbers.

{{+}}Tutorial 3.6.1, 3_6_1{{+}}

## Arrays and Loops

Arrays can also be initialized using for-loops. This is how you should initialize any big array programmatically:

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

int main() {
    int arr[10];
    for(int i = 0; i < 11; i++) {
        // this array stores integers 1 - 10
        arr[i] = i + 1;
    }
```
{{ site.data.alerts.end }}

### Exercise 3.6.2:

- Write a program that asks a user to enter 5 numbers, puts those numbers in an array, and then prints out the numbers in the array backwards. Hint: use a loop that counts backwards.

{{+}}Tutorial 3.6.2, 3_6_2{{+}}

{{-}}Classes and Objects, virtual/programming_objects.md, Next{{-}}
