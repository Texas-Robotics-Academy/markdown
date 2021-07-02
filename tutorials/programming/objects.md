---
title: "Classes and Objects"
tags: [c++]
keywords: c++
sidebar: tutorials
permalink: objects.html
---

## Classes

Sometimes we want to group different kinds of data together.

For example, think about a bank account. What kind of information does your bank account store about you? 

1. Your bank account number (an integer)
2. Your account balance (a float).
3. It also stores your name and address (both strings).

Often we want to group related data single construct, and we can do that with <b>objects</b>.

A <b>class</b> defines a type of object, the variables inside the object (such as bank account number and balance), and functions you can perform on the object (such as `deposit()` and `withdraw()`). So we begin by defining a class.

To start an object, type the keyword `class` and then choose a class name.

{{ site.data.alerts.tip }}
Though not required, a common convention followed by programmers is to begin class names with an uppercase letter).
{{ site.data.alerts.end }}

## A Skeleton of a Class
 For our bank account example, we'll name the class `BankAccount`:

```cpp
class BankAccount {

};
```

A class definition is encompassed by curly braces and has a trailing semi-colon.


## Member Variables
Now we need to add some variables.

Variables inside a class are called <b>member variables</b> or <b>attributes</b>.

The member variables for this class are:

1. account number
2. account balance
3. name
4. address

Adding these to our skeleton definition we get the following:

```cpp
class BankAccount {
     int accountNumber;
     float accountBalance;
     string name;
     string address;
};
```

{{ site.data.alerts.tip }}
Notice that the variables are declared in the same way as before, indicating the type and giving them descriptive names.
{{ site.data.alerts.end }}

## The Public Keyword

Let's suppose that we want to be able to access the variables belonging to a class. By default, they cannot be accessed outside of the scope of the class.

The `public` keyword indicates that the member variables (and functions—we'll add those later) that follow are available to the rest of the program to use.

```cpp
class BankAccount {
  public:
     int accountNumber;
     float accountBalance;
     string name;
     string address;
};
```

{{ site.data.alerts.tip }}
You can also declare a class's variables and functions to be `private`, which will be covered later.
{{ site.data.alerts.end }}

## Constructors
In order to create a `BankAccount` object, we first need to define a constructor.

The constructor is a piece of code that executes when a new object of this class is created. Inside the constructor, we set initial values for any member variables we have, otherwise our program may not work as we intend.

A constructor is defined in the the same way as a function; the only differences are:

1. The name of the constructor must match the name of the class
2. The constructor has no return type

For a brand new `BankAccount`, when we don't yet know anything about the data that will be put into it, default values of zeroes and empty strings will be fine; we can always set them to something else later. Thus, our `BankAccount` constructor is defined as follows:

```cpp
class BankAccount {
  public:
      int accountNumber;
      float accountBalance;
      string name;
      string address;

      BankAccount() {
          accountNumber = 0;
          accountBalance = 0.0;
          name = "";
          address = "";
      }
};
```

We have now defined a basic data structure that holds bank account information, and so we can now write a program that creates a BankAccount object and sets the values of its fields.

{{ site.data.alerts.tip }}
Just like functions must be declared before we can use them (appearing before their first use in the source code), classes must be declared before they are used to create objects.
{{ site.data.alerts.end }}

```cpp
#include <iostream>
using namespace std;

class BankAccount {
  public:
     int accountNumber;
     float accountBalance;
     string name;
     string address;

      BankAccount() {
          accountNumber = 0;
          accountBalance = 0.0;
          name = "";
          address = "";
      }
};


int main() {
     BankAccount alisonBankAccount; //make a bankAccount for Alison
     alisonBankAccount.accountNumber = 14538;  //assign the account a number
     alisonBankAccount.accountBalance = 1000000.01;  //give Alison some money
     alisonBankAccount.name = "Alison Norman";  //assign name and address
     alisonBankAccount.address = "1600 Pennsylvania Avenue NW Washington, DC 20500";
}
```

Look at the first line in main. We've created a `BankAccount` object called `alisonBankAccount`, and it has been initialized using the default constructor.

## Dots

We use the dot to access and set the public variables of an object, as seen in the remaining lines in `main` above.

In dot notation, we access member variables by first writing the name of the object (e.g., `alisonBankAccount`), then a dot, and then the name of the field we want (e.g., `accountNumber`).

## Multiple Objects

We can create multiple different `BankAccounts` and populate them all with different balances and information.

For example, let's say that in addition to Alison's bank account, we'll make an account for Bob Bobson.

Here's the same code as above, but now we've added a second instance of the `BankAccount` class:

```cpp
//make two different bank accounts
BankAccount alisonBankAccount;
BankAccount bobBankAccount;

//assign two different account numbers
alisonBankAccount.accountNumber = 14538;  //assign the account a number
bobBankAccount.accountNumber = 54324;

//assign different account balances
alisonBankAccount.accountBalance = 1000000.01;
bobBankAccount.accountBalance = 2.52;

//give Bob some money to get out of debt
//i.e. add 300.95 to the current value of accountBalance
bobBankAccount.accountBalance += 300.95;

cout << "Bob has $" << bobBankAccount.accountBalance << ".  Yay Bob!\n";
```

We can give Alison and Bob's `BankAccount` objects completely different information, and we can also modify the values that the fields hold. Notice how Bob made a timely deposit with the line:

`bobBankAccount.accountBalance += 300.95;`

The += operator means that you increase the value of the variable to the left of the += by the value on the right side of the += and save it as the same variable. In other words, the following two lines are equivalent:

`bobBankAccount.accountBalance += 300.95;`

`bobBankAccount.accountBalance = bobBankAccount.accountBalance + 300.95;`

These objects do a great job of cleaning up our code—consider having to keep track of Alison and Bob's bank account info without them and what happens when we want to add a third bank account—all those variables add up!

{{ site.data.alerts.tip }}
Have you switched drivers recently? Frequently enough? Don't forget to switch drivers and update your pair programming log.
{{ site.data.alerts.end }}

### Exercise 3.4.1:

- Using this code as a base, add some money to Alison's account and then output her balance.

## The Private Keyword

There is another keyword that is the cousin of `public`, and that is `private`.

Private member variables can only be accessed the object itself—in our case, our `BankAccount` objects.

There are a number of reasons to declare member variables as private, one of which is to maintain quality control on their values—so that account balances can't be set to negative, for instance. In general, you will want to declare variables and functions necessary for the inner workings of the class private and make public the variables and functions necessary for object to be useful to the rest of the program.

Consider the usefulness of using public functions to modify private data, as opposed to leaving the data public. What if we wanted to apply the same set of checks to make sure the account balance is always updated properly—for example, checking for overdrafts or account deposit limits. With our data safely hidden behind the private wall and the use of functions, we can say with confidence our bank account balances are correct.

Returning to our `BankAccount` class, let's go ahead and declare our member variables as private, as shown below.

```cpp
class BankAccount {
  public:
      BankAccount() {
          accountNumber = 0;
          accountBalance = 0.0;
          name = "";
          address = "";
      }
  private:
     int accountNumber;
     float accountBalance;
     string name;
     string address;
};
```

## Member Functions
Now that these variables are private, our object is actually fairly useless right now. We left the constructor public, so we can create new objects, but all our data is inaccessible from outside the class because it's declared private. To make our object useful, we'll introduce member functions, which define actions that can be performed on or with the member variables.

Consider what behavior a `BankAccount` should exhibit. What sorts of actions are necessary? [Think a minute and then read on!]

People need to be able to deposit to and withdraw from their accounts, as well as see their current account balance. The latter we can solve with a simple `getAccountBalance` function that just returns the value stored in `accountBalance`. The deposit and withdraw operations are a little more complex; both modify the account balance by a given amount. What might the deposit function look like? Would it take any arguments? What kind? Does it need to return anything? [Again, think a minute before continuing!]

`deposit()` would need a float as an argument, which is the amount being deposited, and then would need to update the `accountBalance` variable appropriately. It doesn't need to return anything. Since this is a member function, we write its instructions inside the class definition, like this:

```cpp
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
      BankAccount() {
          accountNumber = 0;
          accountBalance = 0.0;
          name = "";
          address = "";
      }
  private:
     int accountNumber;
     float accountBalance;
     string name;
     string address;
};
```

Everything under the public keyword and above the private keyword is our class's public members, and everything below the private keyword is the class's private members. We want both functions to be public; they are the rest of the program's interface with our `BankAccount` data.

Now when we want to deposit money in main, we won't need to type:

 `bobBankAccount.accountBalance += 300.95;`

Instead, we'll be able to say:
 `bobBankAccount.deposit(300.95);`

Thus, our modified main looks like this:

```cpp
int main(){

   BankAccount alisonBankAccount;
   BankAccount bobBankAccount;
   bobBankAccount.deposit(300.95);
}
```

There are a few new things to note.

The syntax for defining a member function is the same as any other function, only it goes inside the class definition.

Inside our member functions we have access to our member variables, as if we had declared them locally inside the function.

Outside of the class definition, we use the dot notation to call an object's member functions; in this case, we have our `bobBankAccount` object, followed by a period, followed by the function call. Just as with the function calls you've made previously, you start with the function name, followed by any arguments wrapped in parentheses.

### Exercise 3.4.2:

- Add another bank account to the example above.
- Deposit $500 dollars into Alison's account.
- Then withdraw $400 from Bob's account and place it in the account you created.
- Then print out the balances from all three accounts.

{{ site.data.alerts.tip }}
You'll need to write the withdraw function. How is it similar to the deposit function? How is it different? What happens if you attempt to withdraw an amount greater than your balance?
{{ site.data.alerts.end }}

{% include callout_red_cup.html task="[Exercise 3.4.1, Exercise 3.4.2]" %}

{{ site.data.alerts.tip }}
Don't forget to switch drivers!
{{ site.data.alerts.end }}

### Exercise 3.4.3:

- Create a superhero class.

The fields should include:

  1. The superhero's name
  2. Arch-nemesis
  3. Weakness
  4. Sidekick 

  (These are all strings).

You are welcome to add some extra fields of your own. Create a default constructor, some methods to set the fields, and a method to print the information in the fields. Then make some instances of the superhero class using your favorite superheroes for inspiration, set the fields appropriately, and print their information.

{% include callout_red_cup.html task="[Exercise 3.4.3]" %}

## Next Step

Proceed to ["Decisions"](decisions.html)
