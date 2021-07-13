# Running from a Thumb Drive

You have hopefully received an envelope from us in the mail containing a USB thumb drive that you can use to participate in the Texas Robotics Academy.

{{ site.data.alerts.warning }}
The thumb drive supports many, but not all computers.

You need to follow our test instructions *even if you do so from the thumb drive,* because the drive may not work on *your* computer.

If the drive does not work on your computer, please proceed to install a Virtual Machine.
{{ site.data.alerts.end }}

{{ site.data.alerts.warning }}
Ubuntu may ask you if you want to upgrade to 20.04.

The answer is *NO.* Doing so will prevent the Texas Robotics Academy software from properly operating.
{{ site.data.alerts.end }}

## Boot to the Drive

1. Reboot your computer
2.  While the machine is rebooting, get to the Boot Menu.
    * The boot menu allows you to pick which device to boot from.
    * This is typically done by hitting F10, F11, or F12 while the machine is rebooting.
        {{ site.data.alerts.tip }}
            * You have to be quick doing this! As soon as your machine starts to reboot, hit F10, F11, and/or F12 repeatedly until you see the boot menu.
            * When you get to the boot menu, select the option for the UEFI Samsung FIT USB drive.
        {{ site.data.alerts.end }}
3. Select "persistent live," from the menu (GRUB).

{{ site.data.alerts.img_50 }}
img/grub_menu.jpg
{{ site.data.alerts.img_50_end }}

4. Once logged
    * Type sudo -s
    * Type cd /etc/apt
    * Type gedit sources.list
    * After every occurrence of "main restricted" add "universe multiverse" so what was "main restricted" now reads "main restricted universe multiverse"

{{ site.data.alerts.note }}
You will need to follow the instructions from "Install the Robotics Academy Software" to set up your thumb drive. This will install software to an operating system running on the thumb drive. It will not install it to the hard drive of your computer.
{{ site.data.alerts.end }}


{{-}}Install the Robotics Academy Software, install_academy, Next, you should go to{{-}}