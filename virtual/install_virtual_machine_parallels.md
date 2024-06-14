# Installing on Mac/Parallels (M1+)

## Download Ubuntu 18.04
1. Download Ubunto 18.04 from https://releases.ubuntu.com/18.04/
    * Select "Desktop Image" and download the 64-bit PC (AMD64) desktop image.
    * This is a large file, and may take some time to download.

## Downloading Parallels and configuring Ubuntu
1. Download and run the Parallels Desktop for Mac Installer and go through the installation prompts on the screen.
* https://www.parallels.com/products/desktop/welcome-trial/
* Make sure you DON'T install Windows when Parallels opens. 
2. After opening Parallels, create an account. Your username and password will be used to log into your account 

    {{ site.data.alerts.img_50 }}
    img/parallels_sign_in.png
    {{ site.data.alerts.img_50_end }}

3. Choose "Install Windows or another OS from a DVD or image file"

    {{ site.data.alerts.img_50 }}
    img/parallels_image2.png
    {{ site.data.alerts.img_50_end }}

4. Then choose the Ubuntu Linux 18.04 desktop image. If it does not appear right away like below click "Choose Manually" and look for it in your Finder.

    {{ site.data.alerts.img_50 }}
    img/parallels_image3.png
    {{ site.data.alerts.img_50_end }}

5. Set Username and Password
    * Username and Display Name: **robocamp**
    * Password: **robocamp2022**

    {{ site.data.alerts.img_50 }}
    img/parallels_image4.png
    {{ site.data.alerts.img_50_end }}

4. Log in with your username and password you created
5. In the bottom left-hand corner there is a menu with 3 rows of 3 dots (9 dots).
    * Click it
    * Type `terminal`
6. A terminal will pop up.
7. Type `sudo apt update`.
8. Type `sudo apt install ubuntu-desktop`
9. Linux is now installed and configured.


{{-}}Install the Robotics Academy Software, virtual/install_academy.md, Next, you should go to{{-}}