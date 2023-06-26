# If and Switch

`if`, `else if`, and `else` statements are used to make a decision based on information we have.

Before learning `if` statements, we must learn logical operators. 

## Logical Operators

Logical operators are used to compare two different variables.

This chart shows the logical operators:

| Logical Operator | Meaning             | Example of True Statement |
|:---:|---|:---:|
|>   | greater than                 | 5 > 4                 |
|>=   | greater than or equal to     | 5 >= 5                |
|<   | less than	                   | 2 < 5                 |
|<=   | less than or equal to        | 2 <= 3                |
|==   | is exactly the same as       | 3 == 3                |
|!=   | is not the same as           | 3 != 5                |


The last two operations, `==` and `!=`, are called equivalency operators because they check if two things are exactly the same, or equivalent. For example, `9 == 9` is true because 9 is exactly the same as 9. Additionally, if we have a variable `myVar` and is set to 9, then `myVar == 9` is true. However, `9 == "nine"` is false because an integer (9) is never exactly the same as a `string` ("nine"). 

The important thing to understand about logical operators is that they return a **bool**. So, if you wrote `5 < 9`, it would be **false**, and if you wrote `10 > 9`, it would be **true**. 

## `if` statements

`if` statements evaluate conditions. **if** something is true, do one thing; **else** do something else. 

Put the **conditional clause**, which is the logical expression we are checking, in parentheses after the word "if". Then put all of the code that we want the computer to execute *if* the conditional clause is true inside of curly braces. After an `if`, we can put an `else if`. `else if` works exactly the same as an `if` but is only checked by the computer if the first `if` statement is false. We can also put an `else` after an `if` or `else if`, which is the code that is executed if all of the previous `if` and `else if` statements are false.

Here is an example of a simple `if` statement use case:

{{site.data.alerts.callout_code_div}}
```
#include <iostream>
using namespace std;

int main() {
    int age = 0;
    cout << "Enter your age:  ";
    cin >> age;

    if (age >= 20) {
        cout << “You are more than 20 years old!” << endl;
    } else if (age >= 13) {
        cout << “Wow, you’re a teenager!” << endl;
    } else {
        cout << “You’ve still got a ways to go young Padawan” << endl;
    }

    return 0;
}
```
{{site.data.alerts.end}}

{{site.data.alerts.note}}
PLEASE ASK QUESTIONS if any of this explanation didn't make sense—-we are happy to explain in person.
{{site.data.alerts.end}}

### Exercise 3.4.1:

- Write a short program, like the one from the example, in which the user enters the number of miles they drive to work. Tell the user if you think that they live "near," "far," or "very far" from their workplace using `if` statements.

{{+}}Tutorial 3.4.1, 3_4_1{{+}}

## Nested `if` statements

You can also put `if` statements inside each other to handle more complex scenarios. Here is an example:

{{site.data.alerts.callout_code_div}}
```
#include <iostream>
#include <string>
using namespace std;

int main() {
    string username;
    string password;

    cout << “Enter username: “ << endl;
    cin >> username;
    cout << “Enter password: “ << endl;
    cin >> password;

    if (username.compare(“Bevo”) == 0) {
        if (password.compare(“bot28”) == 0) {
            cout << “You have successfully logged in!” << endl;
        } else {
            cout << “Incorrect password, please try again” << enld;
        }
    } else {
        cout << “Incorrect username, please try again” << endl;
    }

    return 0;
}
```
{{site.data.alerts.end}}

{{site.data.alerts.note}}
Notice that we are using the function `compare()` to compare two strings. This is how string comparisons should be done in C++.

If you would like to use this method in your program, be sure to `#include <string>` in your program. 
{{site.data.alerts.end}}

## AND, OR, and NOT operators

AND and OR operators let us check two conditions in the same `if` statement. There are three types of conditional operators - the **and operator** `&&`, the **or operator** `||`, and the **not operator** `!`. 

### The AND Operator

The **and operator** combines two logical expressions and checks if both are true. If both conditions are true, it evalutes to true; otherwise, it evaluates to false.

```
int x = 1;
int y = 2;

if ((x == 1) && (y == 2)) {
    // code in this if statement WILL execute, because both conditions evaluated to true
}

if ((x == 2) && (y == 2)) {
    // the first condition evaluates to false, so the whole statement is false
    // code here will NOT execute
}

if ((x == 2) && (y == 3)) {
    // both conditions are false, so code here will not execute
}
```

### The OR Operator

The **or operator** checks if ONE of two separate conditions returns true. If either condition is true, it evaluates to true; otherwise, it evaluates to false.

```
int x = 1;
int y = 2;

if ((x == 1) || (y == 2)) {
    // code in this if statement WILL execute, because both conditions evaluated to true
}

if ((x == 2) || (y == 2)) {
    // code here WILL execute because the second condition evaluates to true
}

if ((x == 2) || (y == 3)) {
    // both conditions are false, so code here will NOT execute
}
```

### The NOT Operator

The **not operator** “flips” the result of some condition from true to false or from false to true. Here is the **not operator** in action:

```
int x = 1;

if (!(x == 1)) {
    // x is equal to 1, so (x == 1) evaluates to true
    // adding the not operator “flips” true to false
    // since the entire condition is false, code inside this if statement will NOT execute
}

if (!(x == 2)) {
    // x is not equal to 1, so (x == 1) evaluates to false
    // adding the not operator “flips” false to true
    // since the entire condition is true, code inside this if statement WILL execute
}
```

Note how we use parentheses to group each conditional, and then group both the conditionals into one statement.

Here's a quick overview of all of the conditional operators.
| Conditional Operator | Meaning | Example of True Statement |
| :--- | :--- | :---: |
| `&&` | Both conditions must be true | `(2 > 1) && (5 != 0)` |
| ``||`` | Either condition must be true | `(1 > 2) || (5 != 0)` |
| `!` | True if the condition is false | `!(1 > 2)` |

### Exercise 3.4.2:

Let’s make a simple program that will help Spock determine if a student is qualified for the Vulcan Academy of Science and Technology based on their math and science grades.

The conditions are as follows:

* A score below 70 in __EITHER__ math or science means automatic denial.
  
* A score of 70 - 79 in __EITHER__ math or science results in them being waitlisted.
  
* A score of 80 - 89 in math results in them being deferred.
* A score of 80 - 89 in science requires a supplementary recommendation letter.
  
* A score of 90 or above in math requires a supplementary science test.
* A score of 90 or above in science requires a supplementary math test.
  
* A score of 90 or above in __BOTH__ math and science guarantees automatic admission.

The program should ask the user to input a math and science score and it should output the admissions result based on the conditions above.

{{+}}Tutorial 3.4.2, 3_4_2{{+}}

## switch-statements

`switch` statements allow the programmer to make a choice based on the value of an integer.

{{ site.data.alerts.callout_code_div }}
```
int main() {

  int option;
  cin >> option;

  switch (option) {
    case 0: // if the variable is equal to 0
        cout << “You get to go to Disney Land!” << endl;
        break;
    case 1: // if the variable equal to is 1
        cout << “You get to go to Universal Studios!” << endl;
        break;
    // default is kind of like the else statement—it occurs if all previous statements were skipped over
    default:
        cout << “You don’t get to go on vacation right now, sorry!” << endl;
        break;
  }

  return 0;
}
```
{{ site.data.alerts.end }}

{{site.data.alerts.note}}
Note the `break` at the end of each case. It is important that you put that break; otherwise, you would just keep going through the cases below!
{{site.data.alerts.end}}

### Exercise 3.4.3

- Write a simple ordering system in which the user picks what they would like to have for lunch using a `switch` statement. For example, `1` might be an apple, `2` might be fugu, and `3` might be a donut.

{{site.data.alerts.note}}
Fugu is a dish made from puffer fish. If is an adventurous Japanese delicacy valued for the skill that a chef must have in order to prepare it. If it is not prepared exactly correctly, the chef may accidentally slice into one of the venom sacs in the puffer fish's skin, or worse, serve the sac to their guest. Only the most highly-trained chefs should prepare this dish, because eating fugu is fatal if the venom is consumed.
{{site.data.alerts.end}}

{{+}}Tutorial 3.4.3, 3_4_3{{+}}

{{-}}Loops, in_person/programming_repetition.md, Next{{-}}
