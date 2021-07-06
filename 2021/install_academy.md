# Install the Robotics Academy Software
{{ site.data.alerts.note }}
These instructions require for you to have Ubuntu 18.04 or 20.04 currently running.
{{ site.data.alerts.end }}

## Installing ROS
* Click on the icon with nine dots in the lower left-hand corner of the screen (3 rows x 3 columns of dots).
* Type “terminal” and click on the “terminal” icon.

{{ site.data.alerts.note }}
* This will be much easier if you open the web browser inside the virtual machine, log in to https://texas-robotics-academy.com from there, and then copy-paste the commands below from *that* browser.
* ctrl-c works as expected from Firefox or Chrome.
* To paste into the terminal, type ctrl-shift-v or right-click.
* Enter the next command when you see the green line with the $ at the end. Only copy one line at a time.
* You will need to enter the password (robocamp2021) when prompted. Nothing will appear on the screen when you do so, not even dots; this is normal.
{{ site.data.alerts.end }}

{{ site.data.alerts.terminal_commands }}
**Adding ROS repositories**
* `sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`
* `sudo apt install curl`
* `curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -`

**Adding Gazebo Packages**
* `sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D2486D2DD83DB69272AFE98867170598AF249743`
* `sudo add-apt-repository http://packages.osrfoundation.org/gazebo/ubuntu-stable`

**Updating and upgrading packages**
* `sudo apt update`
* `sudo apt upgrade -y`
* `sudo apt install ros-noetic-desktop-full`

**Setting up dependencies for ROS**
* `sudo rosdep init`
* `rosdep update`

**Installing Visual Studio Code**
* `sudo snap install --classic code`

**Adding Synaptic, in case you have problems**
* `sudo apt install synaptic`

**Adding Google Chrome**
* `wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb`
* `sudo apt install -y ./google-chrome-stable_current_amd64.deb`


**Adding tools and libraries you will need**
* `sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential`
* `sudo apt install python3-catkin-tools`
* `sudo apt install python3-osrf-pycommon`
* `sudo apt install libgtk-3-dev libncurses5-dev`
* `sudo apt install git`

**Setting up ROS to start every time you log in**
* `source /opt/ros/noetic/setup.bash`
* `echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc`
* `source ~/.bashrc`

**Building the Robotics Academy Workspace and Packages**
* `cd`
* `mkdir catkin_ws`
* `cd catkin_ws`
* `mkdir src`
* `cd src`
* `catkin_init_workspace`
* `git clone https://github.com/Texas-Robotics-Academy/texas_robotics_academy.git`
* `cd ..`
* `catkin build`

**Setting up your catkin workspace to start every time you log in**
* `cd`
* `pwd`
* `gedit ~/.bashrc`
* Add a line at the end of the file. It should say
* source <put the output of pwd here>/catkin_ws/devel/setup.bash
* Save the file and close gedit.
* Close and reopen your terminal. ROS will be ready when you re-open the terminal.

{{ site.data.alerts.terminal_commands_end }}






{{-}}Test Your Installation, install_test, Next, you should go to{{-}}