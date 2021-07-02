---
title: "Decisions"
tags: [c++]
keywords: c++
sidebar: tutorials
permalink: decisions.html
---

In this section, we're going to learn how to control the flow of a C++ program. Sometimes, you want your program to do one thing if certain conditions are met and to do another thing if other conditions are true. We make decisions and control the flow of the program using logical expressions and if-else statements.

Let's imagine we have a program that helps police officers in a town give speeding tickets to drivers based on how fast the driver was going. In this imaginary town, the speed limit is 40 mph, but there are extra penalties if a person goes over 60 mph.

Here's how the program will work: the policeman (the user) enters the speed of a vehicle in the program. If the vehicle was going over 40 mph, the driver gets a $100 speeding ticket. But, if the vehicle was going over 60 mph, the driver gets charged $250. If the vehicle was going 40 mph or under, the driver doesn't get a ticket. The program will display the fine to the user.

## Logical Operators

In order to do this, we will need to test the speed that the user types in (we'll save this to a variable called `driverSpeed` and see if it is greater than 40, and then see if it is also greater than 60. Just like we would in math, we can write this expression using the greater than/less than symbols and store it in a variable:

`isSpeeding = driverSpeed > 40;`

In C++, the above statement can either be true or false, depending upon the value of `driverSpeed`, so `isSpeeding` will either be true or false. A variable that is either true or false is called a `boolean`. In C++ , a boolean that is true displays as a 1, and a `boolean` that is false displays as a 0 when you print it out to the screen. So, in our line of code above, if the value of the variable `driverSpeed` is 20, and you printed out `isSpeeding`, you would see a 0, because 20 is not greater than 40 and thus the statement is false.

The following chart shows all the logical operators, most of which should be familiar to you from math class:

|Logical Operator |Meaning             |Example of True Statement|
|------:|------------------------------|:-----------------------:|
|`>``   | greater than                 | `5 > 4`                 |
|`>=`   | greater than or equal to     | `5 >= 5`                |
|`<``   | less than	                   | `2 < 5`                 |
|`<=`   | less than or equal to        | `2 <= 3`                |
|`==`   | is exactly the same as       | `3 == 3`                |
|`!=`   | is not the same as           | `3 != 5`                |

The last two operations, `==` and `!=`, are called equivalency operators because they check if two things are exactly the same, or equivalent. For example, 9==9 is true because 9 is exactly the same as 9. Additionally, if we have a variable `myVar` and is set to 9, then `myVar==9` is true. However, 9=="nine" is false because an integer (9) is never exactly the same as a `string` ("nine"). In general in C++, you cannot use logical operators to compare strings at all.

## If-statements

To test values and perform a set of instructions (or not) based on the result, we use if statements, which are used in programming exactly the same way we use it in real life. "If" something is true, we do one thing; "else" (otherwise) we do something else. To come back to the speeding ticket program we described above, we could test whether the variable `driverSpeed` is greater than 40 by using the following syntax:
```cpp
if (driverSpeed > 40){
   ticketPrice = 100;
}
else{
   ticketPrice = 0;
}
```

When we use if statements, we put the conditional clause, which is the logical expression we are checking or testing, in parentheses after the word "if". Then we put all of the code that we want the computer to execute if the conditional clause is true inside of curly braces. After an `if`, we can have: an `else if`, which works exactly the same as an `if` but is only checked by the computer when the if statement is false; an else, which is the code that is executed if the `if` statement is false, or nothing.

{% include note.html content="Please ask questions if any of this explanation didn't make sense—-we are happy to explain in person. (Just turn your cups to red!)" %}

We now know everything we need to be able to write the speeding ticket program. We will use an if-else pattern for this program, so we will first check if the speed is greater than 60, and if that is false we will check if the speed is greater than 40, and if that is also false, then we will give a $0 speeding ticket.

```cpp
#include <iostream>
using namespace std;

int main(){

   int driverSpeed, ticketPrice;

   cout << "Hello policeman.  Enter the speed of the vehicle:";
   cin >> driverSpeed;

   if (driverSpeed > 60){        //First check if driver is excessively speeding
      ticketPrice = 250;
   }
   else if (driverSpeed > 40) {  //Then check if driver was going over 40mph
      ticketPrice = 100;
   }
   else{                         //If neither of those were true, the driver wasn't speeding
      ticketPrice = 0;
   }

   cout << "The ticket is $" << ticketPrice << ".\n";
}
```

{{ site.data.alerts.tip }}
  <ul>
  <li>In the above code we use, \n, which will also give you a new line, like endl</li>
  <li>\n is one of a set of what are called "escape characters"</li>
  </ul>
{{ site.data.alerts.end }}

### Exercise 3.5.1:

- Modify the above code so that it prints out a separate message for each different level of ticket.

For example, if the driver was going over 60 mph, the program could print "You should severely punish the driver for endangering people!" and for a non-speeding ticket, the program could print, "Congratulate the driver on maintaining a safe speed."

{{site.data.alerts.callout_red_cup}}
[Exercise 3.5.1]
{{site.data.alerts.end}}

Thanks for enabling better communication. Don't forget to switch drivers!

## Nested if-statements

You can also nest if-statements inside each other. For example, let's say that there is an additional law about wearing seat belts in our imaginary town. If you are speeding and you are also not wearing a seat belt, you get fined an additional $55. We can add this into our code like this:

```cpp
   [...] // ignoring the beginning stuff

   int driverSpeed, ticketPrice;
   string wearingSeatbelt;     //string variable

   //get speed
   cout << "Hello policeman.  Enter the speed of the vehicle:";
   cin >> driverSpeed;

   //user will type y or n
   cout << "Was the driver wearing a seat belt? y or n:";
   cin >> wearingSeatbelt;

   //First check if driver is excessively speeding
   if (driverSpeed > 60){
      //set the initial ticket price to 250
      ticketPrice = 250;

      //if the speed is over 60 AND
      //the driver wasn't wearing a seat belt
      if (wearingSeatbelt == "n"){
         //add 55 to the old ticket price (250+55=305)
         ticketPrice = ticketPrice + 55;
      }
   }
   [...]  //rest of the program
```

You can also check if two or more conditions are both true in the same if-statement. You do this by using &&. So you can say,
//true if both conditionals are true

```cpp
if ((driverSpeed > 60) && (wearingSeatbelt == "n")){
   ticketPrice = 305;  //250 + 55
}
```

If BOTH the first clause (`driverSpeed > 60`) and the second clause (`wearingSeatbelt == "n"`) are true, then the whole conditional is true. If either are false, the whole thing is false. There is also an "or" operator (`||`), which is true if either or both of the conditions are true:

```cpp
// true if one or both conditionals are true
if ((driverSpeed > 60) || (wearingSeatbelt == "n")){
   cout<<"You broke the law, buddy!\n";
}
```

Note how we use parentheses to group each conditional, and then group both the conditionals into one statement.
Finally, there is the not operator (!), which negates a conditional clause (again, note the parentheses!):

```cpp
if (!(wearingSeatbelt == "n")){
   cout << "The driver was wearing a seatbelt!\n";
}
```

### Exercise 3.5.2:

- Finish implementing the seat belt law for the driver who goes over 40mph (just follow the format above). Then come up with another law and add it to your code. Be as creative and ridiculous as you want, and if you need help, ask for it!

{{site.data.alerts.callout_red_cup}}
[Exercise 3.5.2]
{{site.data.alerts.end}}

## Switch-statements

Switch-statements allow you to check the value of a variable against many cases in a compact way. Say you want to write a program that prints out "hello" in different languages based on an input language code. Writing an if-statement (or nested if-statement) for every language sounds tedious. However, you only need to write one switch-statement for all the cases:

```cpp
[...] // the initial stuff

int language;
cin >> language;

switch (language) {
  case 0: // if the language code is 0
      cout << "Hello\n"; // print out "Hello" in English
      break; // This terminates the switch so we don't check all the other cases.
  case 1: // if the language code is 1
      // do something else
      break;
  // Have as many cases as you want
  default:
      // do something if none of the cases above apply. This is optional.
}
```

### Exercise 3.5.3

- Complete the example above so that when the program runs, a user can type a number between 0 to 4, and get a greeting back in one of the five languages you chose.

{{site.data.alerts.callout_red_cup}}
[Exercise 3.5.3]
{{site.data.alerts.end}}

## Next Step

Proceed to ["Repetition"](repetition.html)
