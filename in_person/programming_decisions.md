# If and Switch

if-else statements enable the programmer to make a decision at a given point during the program’s operation.

Before learning if-statements, we must learn logical operators. 

## Logical Operators

Logical operators are used to compare two different variables.

{{site.data.alerts.tip}}
You cannot use logical operators to compare strings in C++!
{{site.data.alerts.end}}

This chart shows the logical operators:

| Logical Operator | Meaning             | Example of True Statement |
|:---:|---|:---:|
|>   | greater than                 | 5 > 4                 |
|>=   | greater than or equal to     | 5 >= 5                |
|<   | less than	                   | 2 < 5                 |
|<=   | less than or equal to        | 2 <= 3                |
|==   | is exactly the same as       | 3 == 3                |
|!=   | is not the same as           | 3 != 5                |


The last two operations, `==` and `!=`, are called equivalency operators because they check if two things are exactly the same, or equivalent. For example, 9==9 is true because 9 is exactly the same as 9. Additionally, if we have a variable `myVar` and is set to 9, then `myVar==9` is true. However, 9=="nine" is false because an integer (9) is never exactly the same as a `string` ("nine"). 

The important thing to understand about logical operators is that they return a **bool**. So, if you wrote `5 < 9`, it would return **false**, and if you wrote `10 > 9`, it would return **true**. 

## if-statements

if-statements evaluate conditions. **if** something is true, do one thing; **else** do something else. 

When we use if statements, we put the **conditional clause**, which is the logical expression we are checking, in parentheses after the word "if". Then we put all of the code that we want the computer to execute *if* the conditional clause is true inside of curly braces. After an `if`, we can have an `else if`, which works exactly the same as an `if` but is only checked by the computer when the if the first statement is false, or an `else`, which is the code that is executed if the `if` statement is false, or nothing.

Here is an example of a simple if-statement use case:

{{site.data.alerts.callout_code_div}}
```
#include <iostream>
using namespace std;

int main() {
    int age = 0;
    cout << "Enter your age:  ";
    cin >> age;

    if(age >= 20) {
        cout << “You are more than 20 years old!” << endl;
    } else if(age >= 13) {
        cout << “Wow, you’re a teenager!” << endl;
    } else {
        cout << “You’ve still got a ways to go young Padawan” << endl;
    }

    return 0;
}
```
{{site.data.alerts.end}}

{{site.data.alerts.note}}
Please ask questions if any of this explanation didn't make sense—-we are happy to explain in person.
{{site.data.alerts.end}}

### Exercise 3.4.1:

- Write a short program, like the one from the example, in which the user enters the number of miles they drive to work. Tell the user if you think that they live "near," "far," or "very far" from their workplace using if statements.

{{+}}Tutorial 3.4.1, 3_4_1{{+}}

## Nested if-statements

You can also nest if-statements inside each other to handle more complex scenarios. Here is an example:

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

    if(username.compare(“Bevo”) == 0) {
        if(password.compare(“bot28”) == 0) {
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

If you would like to use this method in your program, be sure to include <string> in your program. 
{{site.data.alerts.end}}

## AND, OR, and NOT operators

AND and OR operators let us check two conditions in the same if statement. The three types of conditional operators - the **and operator** &&, the **or operator** ||, and the **not operator** !. 

### The AND Operator

The **and operator** checks if two separate conditions both return true. If so, then it returns, true, otherwise it returns false.

```
int x = 1;
int y = 2;

if((x==1) && (y==2)) {
    // this will enter the if statement, because both the conditions evaluated to true
}

if((x==2) && (y==2)) {
    // the first condition evaluates to false, so the whole statement is false. We won’t enter the      
    // if-statement
}

if((x==2) && (y==3)) {
    // both conditions are false, so we won’t enter this if-statement
}
```

### The OR Operator

The **or operator** checks if ONE of two separate conditions returns true. If so, it returns true, otherwise it returns false.

```
int x = 1;
int y = 2;

if((x==1) || (y==2)) {
    // this will enter the if statement, because both the conditions evaluated to true
}

if((x==2) || (y==2)) {
    // we will still enter the if-statement because the second condition evaluates to true
}

if((x==2) || (y==3)) {
    // both conditions are false, so we won’t enter this if-statement
}
```

### The NOT Operator

The **not operator** “flips” the result of some condition. Here is the **not operator** in action:

```
int x = 1;

if(!(x==1)) {
    // x is equal to 1, so we get true, but the not operator would “flip” true to false, so we won’t 
    // enter the if-statement
}

if(!(x==2)) {
    // x is not equal to 1, so we get false, but the not operator would “flip” false to true, so we 
    // would enter the if-statement
}
```

Note how we use parentheses to group each conditional, and then group both the conditionals into one statement.

Here's a quick overview of all of the conditional operators.
| Conditional Operator | Meaning | Example of True Statement |
| :--- | :--- | :---: |
| `&&` | Both conditions must be true | `(2 > 1) && (5 != 0)` |
| `||` | Either condition must be true | `(1 > 2) || (5 != 0)` |
| `!` | True if the condition is false | `!(1 > 2)` |

### Exercise 3.4.2:

Let’s make a simple program that will help Spock determine if a student is qualified for the Vulcan Academy of Science and Technology! Here are the conditions:

If a student scored above a 97 in both math and science, they’re automatically in
If a student scored above a 90 in math, they need to take the supplementary science test
If a student scored above a 90 in science, they need to take the supplementary math test
If a student scored below 90 but above 80 in math, they should be deferred
If a student scored below 90 but above 80 in science, they should submit a supplemental recommendation letter
If a student scored below 80 but above 70 in both math and science, put them on the waitlist
If a student did not score 70 or above, they should try again next year

{{+}}Tutorial 3.4.2, 3_4_2{{+}}

## switch-statements

switch statements allow the programmer to make a choice based on the value of an integer. They make a choice, like if statements do, but the choice is from a list of options defined by the programmer

{{ site.data.alerts.callout_code_div }}
```
int main() {

  int option;
  cin >> option;

  switch (option) {
    case 0: // if the option is 0
        cout << “You get to go to Disney Land!” << endl;
        break;
    case 1: // if the option is 1
        cout << “You get to go to Universal Studios!” << endl;
        break;
    // Have as many cases as you want
    default:
        cout << “You don’t get to go on vacation right now, sorry!” << endl;
        break;
  }

  return 0;
}
```
{{ site.data.alerts.end }}

{{site.data.alerts.note}}
Note the `break` at the end of each case. It is important that you put that break, otherwise you would just keep going through the cases below!
{{site.data.alerts.end}}

### Exercise 3.4.3

- Write a simple ordering system in which the user picks what they would like to have for lunch using an `if` statement. For example, `1` might be an apple, `2` might be fugu, and `3` might be a donut.

{{site.data.alerts.note}}
Fugu is a dish made from puffer fish. If is an adventurous Japanese delicacy valued for the skill that a chef must have in order to prepare it. If it is not prepared exactly correctly, the chef may accidentally slice into one of the venom sacs in the puffer fish's skin, or worse, serve the sac to their guest. Only the most highly-trained chefs should prepare this dish, because eating fugu is fatal if the venom is consumed.
{{site.data.alerts.end}}

{{+}}Tutorial 3.4.3, 3_4_3{{+}}


{{-}}Loops, in_person/programming_repetition.md, Next{{-}}