# Decisions
In this section, we're going to learn how to control the flow of a C++ program. Sometimes, you want your program to do one thing if certain conditions are met and to do another thing if other conditions are met. We make decisions and control the flow of the program using logical expressions and if-else statements.

Earlier, we asked you how the `withdraw` function might be different from the `deposit` function for your `BankAccount` class. The difference is that you cannot withdraw more money than you have! 

You might not know this, but most banks have a minimum balance requirement as well - if your account doesn't stay above the minimum balance, you get charged a fee.

Here's how the `withdraw` function will work: The function receives an amount of money to withdraw. If the resulting balance would be less than zero, we print a message saying that this is an invalid amount of money to withdraw, and don't change the balance. If the amount to withdraw is less than the current balance, but would result in being less than the minimum balance requirement, we warn the user that they aren't meeting the requirement, and subtract a fee from their account. If the amount to withdraw is less than the current balance and still results in the account meeting the minimum balance requirement, we simply report the remaining balance.

## Logical Operators

In order to do this, we will need to test the amount being withdrawn by the user. Let's call the variable `request`, since they are requesting to withdraw money. We will want to see if the amount is greater than the current balance, and then store that as a variable:

```cpp
isValidRequest = (accountBalance - request) > 0;
```

In C++, the above statement can either be true or false, depending upon the values of `accountBalance` and `request`, so `isValidRequest` will either be true or false. A variable that is either true or false is called a **boolean**. 

In C++, we can represent booleans in multiple ways: as an `int` type, or as a `bool` type. A boolean that is true displays as a 1, and a `boolean` that is false displays as a 0 when you print it out to the screen. 

In our line of code above, if the value of `accountBalance - request` is 20, and you printed out `isValidRequest`, you would see a 1, because 20 is greater than 0 and thus the statement is true.

The following chart shows all the logical operators, most of which should be familiar to you from math class:


| Logical Operator | Meaning             | Example of True Statement |
|:---:|---|:---:|
|>   | greater than                 | 5 > 4                 |
|>=   | greater than or equal to     | 5 >= 5                |
|<   | less than	                   | 2 < 5                 |
|<=   | less than or equal to        | 2 <= 3                |
|==   | is exactly the same as       | 3 == 3                |
|!=   | is not the same as           | 3 != 5                |


The last two operations, `==` and `!=`, are called equivalency operators because they check if two things are exactly the same, or equivalent. For example, 9==9 is true because 9 is exactly the same as 9. Additionally, if we have a variable `myVar` and is set to 9, then `myVar==9` is true. However, 9=="nine" is false because an integer (9) is never exactly the same as a `string` ("nine"). 

{{site.data.alerts.tip}}
In general, you cannot use logical operators to compare strings at all in C++!
{{site.data.alerts.end}}

## If-Statements

To test values and perform a set of instructions (or not) based on the result, we use **if statements**, which are used in programming exactly the same way we use it in real life. **If** something is true, we do one thing; **else** (otherwise) we do something else. To come back to the bank account program we described above, we could test whether `accountBalance - request` is greater than the minimum balance by using the following syntax:

{{ site.data.alerts.callout_code_div }}
```
double newBalance = accountBalance - request;

if (newBalance <= 0){
 return; // Don't withdraw anything, because the balance would be invalid
}
else{
  accountBalance = newBalance; // Update the balance
}
```
{{ site.data.alerts.end }}

When we use if statements, we put the **conditional clause**, which is the logical expression we are checking or testing, in parentheses after the word "if". Then we put all of the code that we want the computer to execute *if* the conditional clause is true inside of curly braces. After an `if`, we can have: an `else if`, which works exactly the same as an `if` but is only checked by the computer when the if statement is false, or an `else`, which is the code that is executed if the `if` statement is false, or nothing.

{{site.data.alerts.note}}
Please ask questions if any of this explanation didn't make sense—-we are happy to explain in person.
{{site.data.alerts.end}}

We now know everything we need to be able to write the withdraw function. We will use an if-else pattern for this program, so we will first check if the remaining balance is greater than 0, and if that is false we will check if balance is greater than our minimum balance, and if that is also false, then we will update our balance.

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

class BankAccount {
  public:
    float getAccountBalance() {
      return accountBalance;
    }

    void deposit(float amount) {
      accountBalance += amount;
    }
    
    void withdraw(float request) {
      double newBalance = accountBalance - request;

      if (newBalance <= 0){
        return; // Don't withdraw anything, because the balance would be invalid
      }
      else if(newBalance < minBalance) {
        accountBalance = newBalance - fee; // Update the balance, but subtract a fee
      }
      else{
        accountBalance = newBalance; // Update the balance
      }

    }

    BankAccount() {
      accountNumber = 0;
      accountBalance = 0.0;
      fee = 50.0;
      minBalance = 100.0;
      name = "";
      address = "";
    }

  private:
    int accountNumber;
    float accountBalance;
    string name;
    string address;
    float minBalance;
    float fee;
      
};

int main(){

    float withdrawRequest;
    BankAccount myAccount;
    myAccount.deposit(1000.00);

    cout << "Hello customer, please enter the amount you would like to withdraw: ";
    cin >> withdrawRequest;

    myAccount.withdraw(withdrawRequest);

    cout << "Your remaining balance is : " << myAccount.getAccountBalance() << endl;
    return 0;
}
```
{{ site.data.alerts.end }}


### Exercise 3.5.1:

- Modify the `withdraw` function so that it prints out a separate message for each kind of withdraw case.

For example, if the user attempts to withdraw more money than they have, you should probably let them know that you didn't change the balance. If a fee is applied, you might want to let the user know how much money the fee was, and what balance they should be maintaining.

Thanks for enabling better communication!

{{+}}Tutorial 3.5.1, 3_5_1{{+}}

## Nested if-statements

You can also nest if-statements inside each other. For example, let's consider what happens if our account has enough money to make the withdraw request, but not enough money to cover the fee. We still don't want the user's account to be negative, so let's just say that in this case, we also don't let them withdraw their money:

{{ site.data.alerts.callout_code_div }}
```
   [...] // ignoring the beginning stuff

    void withdraw(float request) {
      double newBalance = accountBalance - request;

      if (newBalance <= 0){
        return; // Don't withdraw anything, because the balance would be invalid
      }
      else if(newBalance < minBalance) {

        if(newBalance <= fee) { // They can't afford the fee
          return; // Don't withdraw anything, because the balance would be negative
        }
        else {
          accountBalance = newBalance - fee; // Update the balance, but subtract a fee
        }
      }
      else{
        accountBalance = newBalance; // Update the balance
      }

    }

  [...]  //rest of the program
```
{{ site.data.alerts.end }}

You can also check if two or more conditions are both true in the same if-statement. You do this by using **and operator** `&&`. So you can say,

{{ site.data.alerts.callout_code_div }}
```
//true if both conditionals are true
if ((newBalance < minBalance ) && (newBalance > fee)){
   accountBalance = newBalance - fee;
}
```
{{ site.data.alerts.end }}

You may have noticed that we have redundant behavior in our code now: we do nothing if `newBalance <= 0`, but we also do nothing if `newBalance <= fee`! But if the second statement is true, then the first statement `newBalance <= 0` is also true! We can modify our first conditional statement to only consider if `newBalance <= fee`.

We're almost done! There's one major problem with our code right now though. What happens if someone tries to `withdraw` a negative amount of money? They end up with more money! 

To avoid this behavior, we will want to do nothing to the balance if our new balance is greater than the original balance. But, we also want to do nothing if the new balance is less than the fee. Since we have the same behavior for *either* condition, we can use the **or operator** `||` to check these conditions:

{{ site.data.alerts.callout_code_div }}
```
// true if one or both conditionals are true
if ((newBalance < fee) || (newBalance > accountBalance)){
  return;
}
```
{{ site.data.alerts.end }}

Note how we use parentheses to group each conditional, and then group both the conditionals into one statement.

Finally, there is the **not operator** (!), which negates a conditional clause (again, note the parentheses!):

{{ site.data.alerts.callout_code_div }}
```
if ((newBalance < fee) || (!(newBalance <= accountBalance))){
  return;
}
```
{{ site.data.alerts.end }}

Here's a quick overview of all of the conditional operators. We've also included this in the documentation for future reference.

| Conditional Operator | Meaning | Example of True Statement |
| :--- | :--- | :---: |
| `&&` | Both conditions must be true | `(2 > 1) && (5 != 0)` |
| `||` | Either condition must be true | `(1 > 2) || (5 != 0)` |
| `!` | True if the condition is false | `!(1 > 2)` |

{{site.data.alerts.tip}}
Did you notice that the last two conditional statements were testing for the same conditions? This is because `a > b` is the same thing as `!(a <= b)`. Try plugging in values for `a` and `b` to see why!
{{site.data.alerts.end}}

### Exercise 3.5.2:

- Our `deposit` function has a similar bug right now with negative numbers. Modify it so that you can only input positive values.
- Most banks also have a deposit limit. Create a member variable `float depositLimit` and modify your `deposit` function to also prevent users from depositing too much money at once.
- Modify the main function to allow users to input a deposit amount. Check the functionality of the previous two steps (i.e, ensure the deposit is not negative and not above the maximum limit).

{{+}}Tutorial 3.5.2, 3_5_2{{+}}

## Switch-statements

Switch-statements allow you to check the value of a variable against many cases in a compact way. Say you want to write a program that let's the user access any of our `BankAccount` functions by pressing a number. Writing an if-statement (or nested if-statement) for every function we have sounds tedious. However, you only need to write one switch-statement for all the cases:

{{ site.data.alerts.callout_code_div }}
```
int main() {

  int option;
  cin >> option;

  BankAccount myAccount;
  myAccount.deposit(100);

  switch (option) {
    case 0: // if the option is 0
        float amount;
        cout << "Enter deposit amount: ";
        cin >> amount; // Store the amount to deposit
        myAccount.deposit(amount);
        break; // This terminates the switch so we don't check all the other cases.
    case 1: // if the option is 1
        // do something else
        break;
    // Have as many cases as you want
    default:
        // do something if none of the cases above apply. This is optional.
  }

  return 0;
}
```
{{ site.data.alerts.end }}

### Exercise 3.5.3

- Complete the example above so that when the program runs, a user can type a 1 to withdraw money from their account, and a 2 to display their current balance.
  - You'll need to store the amount to withdraw in a similar way to how we've stored the amount to deposit in the 0 case.

{{+}}Tutorial 3.5.3, 3_5_3{{+}}


{{-}}Repetition, programming_repetition, Next{{-}}