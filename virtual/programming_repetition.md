# Loops - Online

Loops run blocks of code that the computer runs over and over they reach a stopping their criteria.

There are two kinds of loops that we will work with: `for` loops and `while` loops.

## for Loops

A `for` loop repeats code a specific number of times. If you know exactly how many times you want some lines of code to repeat, you'll want to use a for-loop. Here is an example:

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

int main() {
    for (int i=0; i<5; i++) {
        cout << "Number = " << i << endl;
    }
}
```
{{ site.data.alerts.end }}

This will print:

{{ site.data.alerts.callout_code_div }}
```
Number = 0
Number = 1
Number = 2
Number = 3
Number = 4
```
{{ site.data.alerts.end }}

Let's dissect this code. The word `for` tells the computer that we are writing a for-loop. Inside the parentheses, we define the number of steps the for-loop should run. 

We first define the loop variable, `int  i = 0`. This simply means there is a variable `i` that is initialized to 0 inside the for-loop.
Then, we define a logical expression that will be checked after each step in the loop. So here, we say that `i` must be less than 5 after each step.
Lastly, we define a “step count” (how much the loop variable, in this case `i`, should increase by). Here we say `i++`, which is a shorthand notation for `i+=1`

Within the **body** of the for loop (the section inside the curly braces), we write some code that will be executed at each step. This is the basic structure of a for-loop, and any of the properties mentioned above can be changed to produce different results. Here is another example:

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

int main() {
    for (int i=5; i>=3; i--) {
        cout << "Number = " << i << endl;
    }
}
```
{{ site.data.alerts.end }}

This will print:

{{ site.data.alerts.callout_code_div }}
```
Number = 5
Number = 4
Number = 3
```
{{ site.data.alerts.end }}

### Exercise 3.5.1:

- Write a loop that prints every third number starting at 15 and going down to 6 (so 6 is included in the loop).

{{+}}Tutorial 3.5.1, 3_5_1{{+}}

## While Loops

While loops continue as long a specified condition is satisfied. 

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

int main() {
    int number = 0;
    cout << “Enter the number 5. If you don't, I'll ask again: “ << endl;
    cin >> number;
    while (number != 5) {
        cout << “Try again: “ << endl;
        cin >> number;
    }
}
```
{{ site.data.alerts.end }}

In this example, the while loop will continue until the user enters 5. As you can see, the while loop can go on forever if the condition is not written properly, resulting in an infinite loop. With that, the structure of a while loop is:

Writing `while` tells the computer we are writing a while loop
Inside the parentheses, we write some condition that must hold for the loop to continue
Inside the curly braces, we write the **loop body**, or any code that we want to execute each step of the while loop. 


### Exercise 3.5.2:

- Create a program that asks the user to enter a number between 5 and 50. If the user enters invalid input, print out a message to the user asking them to try again and keep getting input from the user until they enter a valid number.

- Bonus: Can you keep track of the number of attempts a user makes to enter a number, and then print it out when they finally enter a valid number?

{{+}}Tutorial 3.5.2, 3_5_2{{+}}


{{-}}Arrays, programming_arrays, Next{{-}}

## Nested Loops

You can also **nest** loops inside one another. Here are some examples:

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

int main() {
    for(int i = 1; i < 3; i++) {
        for(int j = 2; j < 4; j++) {
            cout << i << “ * “ << j << “ = “ << i * j << endl;
        }
    }
}

/* OUTPUT
1 * 2 = 2
1 * 3 = 3
2 * 2 = 4
2 * 3 = 6 */
```
{{ site.data.alerts.end }}

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

int main() {
    int i = 1;
    int j = 2;
    while(i < 3) {
        while(j < 4) {
            cout << i << “ * “ << j << “ = “ << i * j << endl;
            i++;
            j++;
        }
    }
}

/* OUTPUT
1 * 2 = 2
1 * 3 = 3
2 * 2 = 4
2 * 3 = 6 */
```
{{ site.data.alerts.end }}

### Exercise 3.5.3:

- Write a program that multiplies all the odd numbers between 1 and 9 (including 9) by all the even numbers between 2 and 10 (including 10) . 

Good work!

{{+}}Tutorial 3.5.3, 3_5_3{{+}}


{{-}}Arrays, virtual/programming_arrays.md, Next{{-}}
