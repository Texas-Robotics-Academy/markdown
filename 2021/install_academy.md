# Install the Robotics Academy Software
{{ site.data.alerts.note }}
These instructions require for you to have Ubuntu 18.04 currently running.
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
**Adding ROS Packages**
* `sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654`
* `sudo add-apt-repository http://packages.ros.org/ros/ubuntu`

**Adding Gazebo Packages**
* `sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D2486D2DD83DB69272AFE98867170598AF249743`
* `sudo add-apt-repository http://packages.osrfoundation.org/gazebo/ubuntu-stable`

**Adding Robocamp Packages**
* `sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4F96EF95D295866724CAEEDA0540E766C789458D`
* `sudo add-apt-repository https://texas-robocamp.github.io/packages-virtual`

**Updating and upgrading packages**
* `sudo apt update`
* `sudo apt upgrade -y`

**Installing software**
* `sudo apt install -y ros-melodic-texas-robocamp-full`
* `sudo snap install --classic code`

**Setting up dependencies for ROS**
* `sudo rosdep init`
* `rosdep update`
{{ site.data.alerts.terminal_commands_end }}

{{ site.data.alerts.note }}
Ubuntu includes Firefox by default. If you would prefer to use Google Chrome, also enter these commands:
		{{ site.data.alerts.terminal_commands }}
		* `wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb`
		* `sudo apt install -y ./google-chrome-stable_current_amd64.deb`
		{{ site.data.alerts.terminal_commands_end }}
{{ site.data.alerts.end }}

{{-}}Test Your Installation, install_test, Next, you should go to{{-}}