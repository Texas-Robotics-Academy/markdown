# Running from a Virtual Machine (Windows or Linux)
The virtual machine that you will use is VMWare. It is available for free. Installation instructions are below.

## Installing VMWare
{{ site.data.alerts.note }}
Installing with VMWare will require 20GB of free space on your hard drive.
{{ site.data.alerts.end }}

## Download Ubuntu 20.04 and VMWare
1. Download Ubuntu 20.04.2 from https://releases.ubuntu.com/20.04/ubuntu-20.04.2.0-desktop-amd64.iso
    * This is a large file, and may take some time to download.
2. Download and run the VMWare Installer and go through the installation prompts on the screen
    * Download VMWare Workstation Player 16.1.2 from https://my.vmware.com/en/web/vmware/downloads/details?downloadGroup=WKST-PLAYER-1612&productId=1039&rPId=66621
    * Run the installer
3. Follow the instructions to install VMWare with defaults selected
    * Continue with default options selected until the “Custom Setup” screen
    * If available, check the option to include the Enhanced Keyboard Driver

        {{ site.data.alerts.img_50 }}
        img/vmwaresetup.png
        {{ site.data.alerts.img_50_end }}
    * Continue with the rest of the setup normally (with default settings)
    * Restart your computer to finish installation

## Create the virtual machine
1. Open VMWare
2. Click “Create a New Virtual Machine” (if the installation screen doesn’t come up automatically)
3. Find and add your downloaded Ubuntu ISO File (drag and drop for Mac)

    {{ site.data.alerts.img_50 }}
    img/vmwizardwindows.png
    {{ site.data.alerts.img_50_end }}
4. Make sure easy install is checked
5. Set Username and Password
    * Username and Display Name: **robocamp**
    * Password: **robocamp2021**
6. Customize your settings
    * The option to set Hard Disk Size will show up in creation process
    * Set Hard disk size to 20 GB
    * Select “Store virtual disk as a single file”

        {{ site.data.alerts.img_50 }}
        img/windowshd.png
        {{ site.data.alerts.img_50_end }}
    * The option to configure settings will pop up during VM creation process, you can do so by clicking “Customize Hardware”

        {{ site.data.alerts.img_50 }}
        img/windowssettings.png
        {{ site.data.alerts.img_50_end }}


    {{ site.data.alerts.note }}
    VMWare may ask if it can access your webcam when it first loads up your OS. You should say "yes."
    {{ site.data.alerts.end }}

    {{ site.data.alerts.note }}
    Upon first booting your Virtual Machine, VMWare will automatically install Ubuntu 20.04.
    {{ site.data.alerts.end }}

    {{ site.data.alerts.note }}
    If you missed the setting to customize your hardware, do not worry! It is easy to fix!
    {{ site.data.alerts.end }}

7. If you got through Ubuntu installation, but have not yet customized your hardware
    * Power down the Ubuntu VM (the icon in the upper right-hand corner).

        {{ site.data.alerts.img_50 }}
        img/vmware_power_down.png
        {{ site.data.alerts.img_50_end }}
    * Restart VMWare. You will see a screen like this. Click on "Ubuntu 64-bit", then "Edit virtual machine settings."
    
        {{ site.data.alerts.img_50 }}
        img/pick_vm.png
        {{ site.data.alerts.img_50_end }}
8. Go to Memory
    * Set to about half of your available RAM
    * Set the amount of RAM to the “Maximum recommended memory”
9. Go to Processors
    * Set processor cores to the maximum number available.
        * When you go above the maximum number that your computer will support, a red exclamation point will show up. It looks like this.

            {{ site.data.alerts.img_50 }}
            img/vmware_processors.png
            {{ site.data.alerts.img_50_end }}
        
10. Go to Display and uncheck “Accelerate 3D Graphics”
    * ...unless you have a discrete GPU. For example, the Nvidia GeForce RTX 3090 is a discrete GPU.
    * Try not to brag about your discrete GPU.
11. Save your settings and launch the VM
12. If prompted to Download/Install VMWare Tools or similar packages, download and install them.
13. Wait for installation to complete automatically, then log in and press next on all the prompts for the “Welcome to Ubuntu” window
    * If prompted to install Software Updates, just close the window.. or install them. We will do a step that installs them.

{{ site.data.alerts.tip }}
When starting the VM, you may get a message *“Cannot connect virtual device because no corresponding device is available on the host."* This is because your machine doesn't have a CD/DVD drive. Press no so that the VM will stop looking for the device upon startup.

You may get a similar message about a hard drive, especially under Linux. Generally, these are safe to ignore.

You will probably get a similar message about swap space. This is also safe to ignore.

You will know if the message is not safe to ignore because your VM will not start.
{{ site.data.alerts.end }}

{{ site.data.alerts.tip }}
Ubuntu will also ask you several first-time setup questions. It's safe to click through "next" on all of them.
{{ site.data.alerts.end }}

Your screen should look something like this when your installation is complete.

{{ site.data.alerts.img_50 }}
img/ubuntudesktop.png
{{ site.data.alerts.img_50_end }}

{{ site.data.alerts.tip }}
Want Ubuntu full-screen? Hit ctrl-alt-enter.

Want it back in windowed mode? Do the same thing.
{{ site.data.alerts.end }}

{{-}}Install the Robotics Academy Software, install_academy, Next, you should go to{{-}}