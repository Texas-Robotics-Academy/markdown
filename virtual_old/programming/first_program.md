# First Program: Hello World
{{ site.data.alerts.callout_synchronize }}
Do this section slowly, so you completely understand it. We will be lecturing ***who will be lecturing? If it's counselors, this is a piece of curricula we need to be on the same page about. May want to make a script.*** along with students performing the tutorial, so if you are ahead and have a question, please wait for the room to catch up or for a period when there is no lecturing.
{{ site.data.alerts.end }}

It's customary when you learn a new programming language, to write a program to display the text "Hello World." Displaying text is often referred to as "printing" it, so we're going to learn how to print "Hello World".

## Main

Most C++ programs begin in a function called *main*.

A **function** is a group of instructions about how to do some task.

The *main* function is the first function that executes when we run our C++ program.

**Code** is software as written in a programming language. Someone who writes code is a **coder**.

Sometimes, code is already written and stored in **libraries.**

Libraries save time by providing code that does common things. When professional programmers write software such as a video game, they use libraries to render the graphics, load files, or control physics. This frees the coders who write the rules of the game to concentrate on that aspect. It also frees the ones who specialize in graphics to continually improve on the graphics code used by all of their users.

The "Hello World" example uses the *iostream* library. *iostream* includes a **stream** called *cout*. A stream is a series of characters - in this case, *cout* allows users to write a series of formatted text characters to the terminal, which is often called **printing** the text.


Ok, we're ready to write our first program! The following commands should look familiar from our Linux tutorial.

{{ site.data.alerts.terminal_commands }}
cd ~/cpp_exercises/3_1
code .
{{ site.data.alerts.terminal_commands_end }}

{{site.data.alerts.tip}}
The line *"code ."* is how we can open up VSCode via the command line interface. The . symbol means that we are talking about the current working directory - in this case, that would be 3_1
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

In general you will enclose header names in angle brackets. When you write your own headers, you will probably enclose them in double quotes. 

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

We only have one command for this program. Here we tell the computer to use *cout* and then put what we want to print after *<<*.

The double left-angle brackets are like an arrow pointing toward *cout*, sending something into it (in this case, *"Hello World"*) to *cout*.

After *"Hello World"* there is `<< endl`, which tells the program to end the line of text and follows it with a **newline**, which literally tells the terminal to go to a new line. This is kind of like hitting *enter* at the end of a line when you're typing text.

We put quotation marks around the words we want to display (this is called a **string**). In cpp, every line of code (ones without braces) ends in a semi-colon.

So, you are telling the computer to send *"Hello World!"* as a string to *cout* to be displayed on the screen.

```cpp
return 0;
```

This last line **returns** the number zero. We will get into what this means in a later tutorial, but for now, we can understand it as telling the computer that our program ran properly.

We then use a closing brace to end the function, and with it, the program.

## Compiling and Executing from the Command Line

Compiling code is the act of turning your code into a program that the machine can **execute** or run.

To compile your code, we will use the GNU C++ compiler, better known as *g++*.

- Go back to your terminal where you should be in ~/cpp_exercises/3_1
  - Use the `cd` command to get there if you aren't there already!

{{ site.data.alerts.terminal_commands }}
g++ ex_3_1.cpp -o HelloWorld
{{ site.data.alerts.terminal_commands_end }}

What does this line do?

*g++* runs the g++ compiler.

*ex_3_1.cpp* is the file to be compiled. In this case, it is the file that we just wrote. In future usages of g++, replace *ex_3_1.cpp* with the file that you intend to compile.

*-o HelloWorld* tells the compiler that the compiled program should be named *HelloWorld*. If you typed *-o MyProgram*, it would name your program *MyProgram*.

Hopefully, your program just compiled.

- Check the output in the terminal to see if the build was a success.
  - If your build is successful, there will be no output.
- Run your program

{{ site.data.alerts.terminal_commands }}
./HelloWorld
{{ site.data.alerts.terminal_commands_end }}


{{ site.data.alerts.note }}
Remember, this is a relative path, so this literally tells the computer, "Run the HelloWorld that is in this directory."
{{ site.data.alerts.end }}

{{ site.data.alerts.callout_synchronize }}
Many of you will have problems right now, so, we'll synchronize to get everyone through their errors.
{{ site.data.alerts.end }}

If you ever forget how to compile a C++ program, we've provided an example in the [documentation](docs.html) that you can always reference in the future.

### Exercise 3.1:

- Modify the Hello World program so that it prints, "Hello <Your Name>!"
    - For example, if your name is Justine, it would display, *Hello Justine!*
- Next, add a second line of text that says, "Programming is actually pretty fun when you get right down to it."

{{site.data.alerts.tip}}
From here on out you will be creating new files for each exercise you do. It would be a good idea to name the files for each exercise according to the exercise name. For example, directory 3_1 will contain exercise ex_3_1.cpp, and directory 3_2 will contain exercises ex_3_2_1.cpp, ex_3_2_2.cpp, and ex_3_2_3.cpp
{{site.data.alerts.end}}

{{+}}Tutorial 3.1, 3_1{{+}}

## Next Step

Proceed to ["Simple Math and User Input"](simple_math_user_input.html).
