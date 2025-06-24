# Exercise 1: Cloning the Exercises

Open a terminal.


{{ site.data.alerts.note }}
Need help opening a terminal? Look back to the slides by clicking on "Welcome!" and navigating to them.
{{ site.data.alerts.end }}

{{ site.data.alerts.terminal_commands }}
echo "export PATH=$PATH:/lusr/opt/firstbytes/arduino-1.8.19" >> ~/.bashrc
{{ site.data.alerts.terminal_commands_end }}

Log out, then log back in.

{{ site.data.alerts.terminal_commands }}
git clone https://github.com/Texas-Robotics-Academy/activities.git
cd activities
code .
arduino &
{{ site.data.alerts.terminal_commands_end }}

You should now have a Visual Studio Code window open and an Arduino window open.

{{+}}Exercise 1, 1{{+}}

{{-}}Exercise 2: Hello World, 2025/ex_2_hello_world.md, Next{{-}}