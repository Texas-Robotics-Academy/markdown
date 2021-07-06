# Testing Your Installation

Open a terminal.

{{ site.data.alerts.note }}
Recall that this can be done from the menu in the lower left-hand corner (the nine dots).

Click the menu, then type "terminal," then click the terminal icon.
{{ site.data.alerts.end }}

{{ site.data.alerts.terminal_commands }}
* `roslaunch texas_robocamp test_world.launch`
{{ site.data.alerts.terminal_commands_end }}

You should see two windows appear. One will have the UT logo and our simulated robot in the middle.

{{ site.data.alerts.img_50 }}
img/successful_install.png
{{ site.data.alerts.img_50_end }}

Open a new terminal by right clicking in the terminal window and clicking “open tab”.

{{ site.data.alerts.terminal_commands }}
* `rosrun texas_robocamp teleop_texbot`
{{ site.data.alerts.terminal_commands_end }}

1. Use the keys listed on the screen to drive the robot around. (You must have this terminal selected for them to work.)
2. At the bottom of the simulator, you will see a bar with a bunch of numbers. Write down the number next to the FPS label
    * It will be changing; write down an approximate value.

{{ site.data.alerts.tip }}
If your FPS is very low (below 10) or you would like to improve it, try resizing the window down.

If this is too small for you to see what's going on, then please let us know *during the setup day on July 5.*
{{ site.data.alerts.end }}

3. If everything looks good, go back to the terminal and press ctrl-c in both windows to shut down the testing system and wait for all the windows to close completely.
    * Once you see a “done” message, you can shut down the virtual machine:
        * Click the arrow in the top-right corner of the screen.
        * Click the power icon.
        * Click Power Off.

{{ site.data.alerts.good_job }}
Congrats! You are set up and configured for camp!
{{ site.data.alerts.end }}

{{ site.data.alerts.important }}
If you had problems and could not complete the install, then please let us know *during the setup day on July 10.*
{{ site.data.alerts.end }}

{{=}}{{=}}