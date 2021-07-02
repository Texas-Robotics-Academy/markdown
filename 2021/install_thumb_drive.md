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

{{ site.data.alerts.note }}
The Thumb Drive comes with all of the Texas Robotics Academy software pre-installed.

You still need to *Test Your Installation* to assure that all features perform properly on your computer.
{{ site.data.alerts.end }}


{{-}}Test Your Installation, install_test, Next, you should go to{{-}}