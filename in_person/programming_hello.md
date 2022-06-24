# Hello World

{{ site.data.alerts.note }}
It's customary when you learn a new programming language, to write a program to display the text "Hello World."

Displaying text is often referred to as "printing" it, so we're going to learn how to print "Hello World".
{{ site.data.alerts.end }}


## Main

C++ programs begin in a function called **main**. You will understand this after a few examples.


{{ site.data.alerts.note }}
- The **main** function is the first function that executes in a C++ program.
- A **function** is a set of instructions for the computer.
- **Code** is software as written in a programming language.
- A **coder** is someone who writes code.
- **Libraries** contain code that has already been written and is usable in other programs.
{{ site.data.alerts.end }}


Libraries save time by providing code that does common things.

The "Hello World" example uses the **iostream** library. iostream includes a **stream** called **cout**. cout allows users to write to the terminal, which is often called **printing**.

{{ site.data.alerts.terminal_commands }}
cd ~/cpp_exercises/3_1
code .
{{ site.data.alerts.terminal_commands_end }}

{{site.data.alerts.tip}}
The line *"code ."* is how we can open up VSCode via the command line interface. The . symbol means that we are talking about the current working directory.
{{site.data.alerts.end}}

In VSCode, make a new file in the 3_1 directory, and name it ex_3_1.cpp. Copy the following program into that file and save it.

{{site.data.alerts.tip}}
To create a new file in VSCode, type *"ctrl+n"*. To save the file, type *"ctrl+s"*
{{site.data.alerts.end}}

{{ site.data.alerts.callout_code_div }}
```
#include <iostream>
using namespace std;

int main(){
  cout << "Hello World!" << endl;
  return 0;
}
```
{{ site.data.alerts.end }}

Let's look at this code line-by-line.

```cpp
#include <iostream>
``` 

This line **includes** `iostream` into our program, making its contents available to our program. `iostream` is what is called a **header** or a **header file**. It contains the code needed to interface a library called the *Standard Input/Output Streams Library*. Including `iostream` allows us to use `cout`.

{{ site.data.alerts.note }}
In general you will enclose header names in angle brackets. 
{{ site.data.alerts.end }}

```cpp
using namespace std;
```

This line tells the compiler that if things are included in the *std* namespace, they don't need to lead the name with *std*. In the program here, *cout* is a part of the *std* namespace. If we did not **use** the *std* namespace, we would write it as `std::cout`.

{{ site.data.alerts.tip }}
For the purposes of this camp, just include *using namespace std* in your programs. Namespacing will become important if you continue programming, but we only use one namespace in this camp.
{{ site.data.alerts.end }}

```cpp
int main(){
```

This next line defines the *main* function. This tells the computer that there is a function called *main* that **returns** an integer (more on this later).

The code for *main*, like the code for all functions, is wrapped in curly braces. We call the code wrapped in braces a **block**. In this line, we are beginning the block with an opening brace.

```cpp
cout << "Hello World!" << endl;
```

Here print using *cout*. Put what should be printed after *<<*.

The double left-angle brackets are like an arrow pointing toward *cout*, sending something into it (in this case, *"Hello World"*) to *cout*.

After *"Hello World"* there is `<< endl`. This tells the program to end the line of text and put any new content on the next line.

The quotation marks indicate that what is inside is a **string**, that is, literal text that we want in the program.

In c++, every line of code (ones without braces) ends in a semi-colon.

```cpp
return 0;
```

We will come back to what **return** means later in the academy. For now, just place it here because it is necessary for the program to execute properly.


## Compiling and Executing from the Command Line

Compiling code turns the code into a program that can be **executed**.

- Go back to your terminal where you should be in ~/cpp_exercises/3_1
  - Use the `cd` command to get there if you aren't there already!

{{ site.data.alerts.terminal_commands }}
g++ ex_3_1.cpp -o HelloWorld
{{ site.data.alerts.terminal_commands_end }}

*g++* runs the g++ compiler.

*ex_3_1.cpp* is the file to be compiled. In this case, it is the file that we just wrote.

*-o HelloWorld* tells the compiler that the compiled program should be named *HelloWorld*.

- Check the output in the terminal to see if the build was a success.
  - If your build is successful, there will be no output.
- Run your program

{{ site.data.alerts.terminal_commands }}
./HelloWorld
{{ site.data.alerts.terminal_commands_end }}


{{ site.data.alerts.note }}
This is a relative path, so this literally tells the computer, "Run the HelloWorld that is in this directory."
{{ site.data.alerts.end }}

## Exercise 3.1:

- Modify the Hello World program so that it prints, "Hello <Your Name>!"
    - For example, if your name is Justin, it would display, *Hello Justin!*
- Next, add a second line of text that says, "Programming is actually pretty fun when you get right down to it."

{{site.data.alerts.tip}}

From here on out you will be creating new files for each exercise you do. It would be a good idea to name the files for each exercise according to the exercise name. For example, directory 3_1 will contain exercise ex_3_1.cpp, and directory 3_2 will contain exercises ex_3_2_1.cpp, ex_3_2_2.cpp, and ex_3_2_3.cpp
{{site.data.alerts.end}}

{{+}}Tutorial 3.1, 3_1{{+}}

{{-}}Simple Math and User Input, in_person/programming_math.md, Next{{-}}