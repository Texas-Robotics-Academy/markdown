# Classes and Objects
Consider this scenario. You and your friends believe that one of you gets called on **way** more often by your teacher. You want to make sure so you write a simple `class`. A class is a type. A variable whose type is a class is called an `object.` A class lets you associate multiple pieces of data together in a single variable

Consider these attributes of the class that will be used to count how often you are called on.

1. Name (`string`)
2. Times called (`int`).

Classes also have `methods` which work just like functions, except that they are able to work on data in the class.

To start defining a class, type the keyword `class` and then choose a class name.

{{site.data.alerts.tip}}
Though not required, a common convention followed by programmers is to begin class names with an uppercase letter).
{{site.data.alerts.end}}

## Class declarations
 For our friends example, we'll name the class `Buddy` (because `friend` is already used in C++):

{{ site.data.alerts.callout_code_div }}
```
class Buddy {

};
```
{{ site.data.alerts.end }}

A class definition is encompassed by curly braces and has a trailing semi-colon.


## Attributes
Now we need to add some attributes.

Variables inside a class are called **member variables** or **attributes**.

The attributes of this class are:

1. name
2. timesCalled

Adding these to our class definition we get the following:

{{ site.data.alerts.callout_code_div }}
```
class Buddy {
  string name;
  int timesCalled;
};
```
{{ site.data.alerts.end }}

{{site.data.alerts.tip}}
Notice that the variables are declared in the same way as before, indicating the type and giving them descriptive names.
{{site.data.alerts.end}}

{{site.data.alerts.tip}}
Note that we use the `string` type here, which means that we must also `#include <string>`
{{site.data.alerts.end}}


## Dots & The Public Keyword

The attributes of a class are accessed using a dot `.`;

By default, you cannot access the attributes of a class from outside the class. This is because they are `private`.


{{ site.data.alerts.callout_code_div }}
```
class Buddy {
  string name;
  int timesCalled;
};


int main() {
  Buddy justin;
  justin.name = "Justin";
  return 0;
}
```
{{ site.data.alerts.end }}

If you try to compile this code, the compiler will not let you, because you are not allowed to access the private attribute `name`.

The `public` keyword indicates that attributes can be accessed from outside of the class.

If you change the code above to read like this, it will work.

{{ site.data.alerts.callout_code_div }}
```
class Buddy {
  public:
     string name;
     int timesCalled;
};


int main() {
  Buddy justin;
  justin.name = "Justin";
  return 0;
}
```
{{ site.data.alerts.end }}


## Constructors
When you first create an object (like `justin` above), you will want to `initialize` the attributes inside of it.

All of your buddies should start out having been called on `0` times, and they should all have names. This can be addressed using a `constructor`.


{{ site.data.alerts.callout_code_div }}
```
class Buddy {
  public:
    string _name;
    int _timesCalled;

    Buddy(string name) {
      _name = name;
      _timesCalled = 0;
    }
};


int main() {
  Buddy justin("Justin");
  return 0;
}
```
{{ site.data.alerts.end }}

The **constructor** executes when a new *instance* (object) of this class is created. Inside the constructor, we set the initial values for any attributes we have.

{{site.data.alerts.note}}
Note that the attributes `name` and `timesCalled` have been changed to `_name` and `_timesCalled`.

Adding an underscore (`_`) to the start of the name of the class attribute helps to differentiate it from the parameter. If the `name` that is changed to `_name` is been changed, the constructor will assume that the parameter `name` is meant whenever `name` is used. The above code, then, would not successfully set `_name` to the argument used in `main()`.
{{site.data.alerts.end}}

A constructor is defined in the the same way as a function; the only differences are:

1. The name of the constructor must match the name of the class
2. The constructor has no return type

## Class Methods
Just like classes can have attributes (like variables in `main` or other functions), they can have methods, which are the equivalent of functions.

Consider the class attribute `_timesCalled`. You could always simply set its value in `main`, but that's kind of silly, because the teacher can not retroactively **uncall** a student.

A method to count the number of times a student is called on could be written like this:

{{ site.data.alerts.callout_code_div }}
```
class Buddy {
  public:
    string _name;
    int _timesCalled;

    Buddy(string name) {
      _name = name;
      _timesCalled = 0;
    }

    void callOn() {
      _timesCalled++;
    }
};


int main() {
  Buddy justin("Justin");
  justin.callOn();
  return 0;
}
```
{{ site.data.alerts.end }}

There are a few new things to note:

  - The syntax for defining a method is similar to that of a function, only it goes inside the class definition.
  - Methods have access to the attributes of a class, even if they are private (more on that below).
  - Outside of the class definition, the dot notation is used to call methods.

## The Private Keyword

There is another keyword that is similar to `public`; `private`.

As stated before, private attributes cannot be accessed from outside the class using the dot notation.

Notice a problem with the program above. Even though the method `callOn()` has been declared, it would still be possible to modify `_timesCalled` from main. This means that it is still possible for the illogical act of retroactively uncalling on a Buddy to occur.

To avoid this, make the class attribute `_timesCalled` private, as follows:

{{ site.data.alerts.callout_code_div }}
```
class Buddy {
  private:
    int _timesCalled;

  public:
    string _name;

    Buddy(string name) {
      _name = name;
      _timesCalled = 0;
    }

    void callOn() {
      _timesCalled++;
    }
};


int main() {
  Buddy justin("Justin");
  justin.callOn();
  return 0;
}
```
{{ site.data.alerts.end }}

Now, _timesCalled cannot be directly accessed from `main()`, and can only be changed by calling `callOn()`.

### Exercise 3.7.1:

- Add a class method to `Buddy` which prints out the name of the buddy and the number of times that they have been called on. For example, if the buddy **Justin** has been called on **5** times, it should print: **Justin has been called on 5 times.**
- Write a for loop to call `callOn()` an object of type `Buddy` **11** times
- Call your print method to show how many times the `Buddy` has been called on.

{{+}}Tutorial 3.7.1, 3_7_1{{+}}


## Multiple Objects
The point of having a class is that you can have multiple objects of the same class.

Suppose that there are three students, **Justin**, **Tiffany**, and **MaryEsther**. A program which instantiates them and has them each called on a different number of times might look like this.

{{ site.data.alerts.callout_code_div }}
```
class Buddy {
  private:
    int _timesCalled;

  public:
    string _name;

    Buddy(string name) {
      _name = name;
      _timesCalled = 0;
    }

    void callOn() {
      _timesCalled++;
    }
};

int main() {
  Buddy justin("Justin");
  Buddy tiffany("Tiffany");
  Buddy maryEsther("MaryEsther");

  for(int i = 0; i < 3; i++) {
    justin.callOn();
  }

  for(int i = 0; i < 5; i++) {
    tiffany.callOn();
  }

  for(int i = 0; i < 9; i++) {
    maryEsther.callOn();
  }

  return 0;
}
```
{{ site.data.alerts.end }}

### Exercise 3.7.2:

Now, put this all together.

- Starting with the existing `Buddy` class, add a method to count how baskets they have scored playing basketball during recess.
- Declare 3 buddies (you can use the ones above)
- Use a for loop to count how many baskets each buddy has scored
- Modify the print method from 3.7.1 to print how many times the buddy has been called, and how many baskets they have scored.
- Use the print method that you have written to print out the information for each buddy.

{{+}}Tutorial 3.7.2, 3_7_2{{+}}

Great! You're now ready to work on the robot.

{{-}}Cloning the Robotics Exercises, robot_cloning, Next{{-}}
