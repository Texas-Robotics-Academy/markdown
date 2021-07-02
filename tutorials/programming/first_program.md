---
title: "First Program: Hello World"
tags: [c++]
keywords: c++
sidebar: tutorials
permalink: first_program.html
---

{% include callout_synchronize.html comment="Do this section at the pace of the slower partner, so both of you completely understand it. We will be lecturing along with students performing the tutorial, so if you are ahead and have a question, please wait for the class to catch up or for a period when there is no lecturing." %}

It's customary when you learn a new programming language, to write a program to display the text "Hello World." Displaying text is often referred to as "printing" it, so we're going to learn how to print "Hello World".

## Main

Most C++ programs begin in a function called `main`.

A <b>function</b> is a group of instructions about how to do some task.

The `main` function is the first function that executes when we run our C++ program.

<b>Code</b> is software as written in a programming language. Someone who writes code is a <b>coder</b>.

Sometimes, code is already written and stored in <b>libraries.</b>

Libraries save time by providing code that does common things. When professional programmers write software such as a video game, they use libraries to render the graphics, load files, or control physics. This frees the coders who write the rules of the game to concentrate on that aspect. It also frees the ones who specialize in graphics to continually improve on the graphics code used by all of their users.

The "Hello World" example uses the `iostream` library. `iostream` includes a <b>stream</b> called `cout`. `cout` allows users to write formatted text to the terminal, which is often called <b>printing</b> the text.

Ok, we're ready to write our first program!

{{ site.data.alerts.terminal_commands }}
cd ~/exercises
mkdir ex04_Hello_World
cd ex04_Hello_World
sublime_text &
{{ site.data.alerts.terminal_commands_end }}

Copy the following program into Sublime.

Save the file as ~/exercises/ex04_Hello_World/HelloWorld.cpp

```cpp
#include <iostream>
using namespace std;

int main(){
  cout << "Hello World!" << endl;
  return 0;
}
```

Look at the code line-by-line.

Compiling is when the computer turns the text written in C++ into the machine code that it can run.

`#include <iostream>` <b>includes</b> `iostream` when compiling the program, making its contents available to our program.

`iostream` is what is a <b>header</b> or a <b>header file</b>. It contains the code needed to interface a library called the "Standard Input/Output Streams Library."

Including `iostream` allows us to use `cout`.

In general you will enclose header names in angle brackets (when you write your own headers, you will probably enclose them in double quotes).

The next line, `using namespace std`; tells the compiler that if things are included in the `std` namespace, that it doesn't need to lead the name with `std`. In the program here, we use `cout`, but if we did not <b>use</b> the `std` namespace, we would write it as `std::cout`.

{{ site.data.alerts.tip }}
For the purposes of this camp, just include `using namespace std` in your programs. Namespacing will become important if you continue programming, but we only use one namespace in this camp.
{{ site.data.alerts.end }}

The next line defines the `main` function by saying `int main()`. This tells the computer that there is a function called `main` that returns an integer (more on this later).

The code for `main`, like the code for all functions is enclosed in curly braces. This is called a <b>block</b>.

We only have one command for this program. We tell the computer to use `cout` and then put what we want to print after `<<`.

The double left-angle brackets are like an arrow pointing toward cout, sending something into it (in this case, `"Hello World"`) to `cout`.

After `"Hello World"` there is `<< endl`, telling the program to end the line of text. If you don't do this, there is no guarantee that your text will show up on the screen, and it will not be followed by a <b>newline</b>, which literally tells the terminal to go to a new line. This is kind of like hitting enter at the end of a line.

We put quotation marks around the words we want to display (this is called a <b>string</b>). In C++, every line of code (ones without braces) ends in a semi-colon.

So, you are telling the computer to send `"Hello World!"` as a string to `cout` to be displayed on the screen.

One last line in our program is `return 0`. This <b>returns</b> the number zero. We will get into what this means in a later tutorial, but for now, we can understand it as telling the computer that our program ran properly.

We then use a closing brace to end the function, and with it, the program.

## Compiling and Executing from the Command Line

Compiling code is the act of turning your code into a program that the machine can <b>execute</b> or run.

To compile your code, we will use the GNU C++ compiler, better known as `g++`.

- Go back to your terminal where you should be in ~/exercises/ex04_Hello_World

{{ site.data.alerts.terminal_commands }}
g++ HelloWorld.cpp -o HelloWorld
{{ site.data.alerts.terminal_commands_end }}

What does this line do?

`g++` runs the g++ compiler.

`HelloWorld.cpp` is the file to be compiled. In this case, it is the file that we just wrote. In future usages of g++, replace `HelloWorld.cpp` with the file that you intend to compile.

`-o HelloWorld` tells the compiler that the program should be named `HelloWorld`. If you typed `-o MyProgram`, it would name your program `MyProgram`.

Hopefully, your program just compiled.

- Check the output in the terminal to see if the build was a success.

- Run your program

{{site.data.alerts.terminal_commands}}
./HelloWorld
{{site.data.alerts.terminal_commands_end}}


{% include note.html content="Remember, this is a relative path, so this literally tells the computer, \"Run the HelloWorld that is in this directory.\"" %}

{% include note.html content="Many things can go wrong when you are programming. Turn your cups to red to get help." %}

{% include callout_synchronize.html comment="Many of you will have problems right now, so, we'll synchronize to get everyone through their errors." %}

## Exercise 3.1:

- Modify the Hello World program so that it prints, "Hello \<Your Name\> and \<Your Partners Name\>".

For example, if your name is Justine and your partner is Justin, it would display, Hello Justine and Justin.

- Next, add a second line of text that says, "Programming is actually pretty fun when you get right down to it."

{{site.data.alerts.callout_red_cup}}
[Tutorial 3.1]
{{site.data.alerts.end}}

## Next Step

Proceed to ["Simple Math and User Input"](simple_math_user_input.html).
