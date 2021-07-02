## Cloning the Robotics Exercises

Just like with the C++ exercises, we have provided you with a directory structure of ROS packages and files in which you will complete the robotics exercises. 

Before we begin, make sure you have the latest version of the packages:

{{site.data.alerts.terminal_commands}}
sudo apt update
sudo apt upgrade
{{site.data.alerts.terminal_commands_end}}

First, you will need to make a **catkin workspace**. In the terminal, enter these commands:

{{site.data.alerts.terminal_commands}}
source /opt/ros/melodic/setup.bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws
catkin init
{{site.data.alerts.terminal_commands_end}}

This should have created a directory named **catkin_ws** that contains another directory named **src**.

In the terminal, navigate into the src folder in your catkin_ws. Then copy the following command:

{{site.data.alerts.terminal_commands}}
git clone https://github.com/texas-robocamp/robocamp_exercises.git
{{site.data.alerts.terminal_commands_end}}

## Next Step

Proceed to ["Robot Programming Introduction"](robot_programming_introduction.html)
