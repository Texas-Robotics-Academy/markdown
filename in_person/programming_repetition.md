# Loops

Loops are used to execute the same block of code multiple times until they reach a stopping criteria.

There are two kinds of loops that we will work with: `for` loops and `while` loops.

## For Loops

A `for` loop repeats code a specific number of times. If you know exactly how many times you want some lines of code to repeat, you'll want to use a loop. Here is an example:

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

int main() {
    for (int i = 0; i < 5; i++) {
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

Let's take a look at the syntax of `for` loops: `for (int i = 0; i < 5; i++) {`

`for (`: This is the starting syntax for a `for` loop. Inside the parentheses, we use 3 elements of code to define the number of times the loop should run. They are as follows

1. `int i = 0; ` We create a variable called `i` to count how many times our loop has run. Let's start at 0. NOTE THE SEMICOLON!!!
2. ` i < 5; ` We define a logical expression that will be checked after each time the loop runs. So here, we say that `i` must be less than 5 after each time. So, this loop will run as long as our counter, `i`, is less than 5. Since we're starting at 0, this loop will run exactly 5 times. NOTE THE SEMICOLON!!!
3. `i++` We increase our counter, `i`, by 1 each time the loop runs, in order to count how many times it has already run. Here we say `i++`, which is the same as `i += 1`.
   
Inside the curly braces, we write the **loop body**, or any code that we want to execute during each repetition of the `for` loop. 

This is the basic structure of a `for` loop, and any of the elements mentioned above can be changed to produce different results. Here is another example:

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

int main() {
    for (int i = 5; i >= 3; i--) {
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


{{site.data.alerts.note}}
PLEASE ASK QUESTIONS about loops! High school CS classes typically spend up to a month learning about loops, but y'all are doing it in only one day! Kudos to you!
{{site.data.alerts.end}}

## While Loops

`while` loops continue as long a specified condition is satisfied. 

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

* Writing `while` tells the computer we are writing a while loop: `while`
* Inside the parentheses, we write some condition that must hold true for the loop to continue: `(number != 5)`. So, this loop will run as long as `number` is not equal to 5.
* Inside the curly braces, we write the **loop body**, or any code that we want to execute during each repetition of the `while` loop. 


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
    for (int i = 1; i < 3; i++) {
        for (int j = 2; j < 4; j++) {
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
    while (i < 3) {
        while (j < 4) {
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

- Write a program, similar to the one above, that multiplies each odd number between 1 and 9 (including 9) by each even number between 2 and 10 (including 10). Output the product of the odd and even number each time you multiply (there should be 25 lines of output)!

Good work!

{{+}}Tutorial 3.5.3, 3_5_3{{+}}


{{-}}Arrays, in_person/programming_arrays.md, Next{{-}}
