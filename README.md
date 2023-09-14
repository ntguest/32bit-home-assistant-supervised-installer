[![hacs_badge](https://img.shields.io/badge/HAss-Installer-blue.svg)](https://www.home-assistant.io/)
[![Donate](https://img.shields.io/badge/donate-Pizza-yellow.svg)](https://www.buymeacoffee.com/ntguest)
[![Donate](https://img.shields.io/badge/donate-Yandex-blueviolet.svg)](https://yoomoney.ru/to/410011383527168)

# 32bit-home-assistant-supervised-installer
Home Assistant supervised and ESPHome installer for 32bit systems.

Описание на русском языке доступно [ЗДЕСЬ](https://github.com/ntguest/32bit-home-assistant-supervised-installer/blob/main/README-RUSSIAN.md)

## Installing Home Assistant Supervised on Debian 12 Bookworm  (Debian 11 Bullseye as well)

This guide will help you to install Home Assistant Supervised, on almost any machine type you choose, even netbooks, nettops and old PCs with 32bit CPU. 

:warning: Using Debian 12 and following a strict set of guidelines available [HERE](https://github.com/home-assistant/architecture/blob/master/adr/0014-home-assistant-supervised.md) will give you a supported installation of Home Assistant Supervised. If you choose at anytime to install additional software to the Debian operating system, your installation will become officially unsupported. Community support via the forums is always available however.

*note: Debian derriatives such as Armbian, OS for Orange PI, etc. is also supported (you may have to edit /etc/os-release and replace with PRETTY_NAME="Debian GNU/Linux 12 (bookworm)"). Ubuntu is HIGHLY NOT RECCOMENDED due to unstable work.

While every effort has been made to ensure this guide complies with [ADR-0014](https://github.com/home-assistant/architecture/blob/master/adr/0014-home-assistant-supervised.md), no guarantee can be made it does now, or in the future.

In this guide, you will be using Debian 11 as the operating system. This type of installation is what is called “headless” and after the installation is complete, you will not need to have a keyboard, mouse or monitor attached, although you can if you prefer.

#### What is Home Assistant Supervised? ####

Home Assistant is a full UI managed home automation ecosystem that runs Home Assistant Core, the Home Assistant Supervisor and add-ons. It comes pre-installed on Home Assistant OS, but can be installed on any Linux system. It leverages Docker, which is managed by the Home Assistant Supervisor plus the added benefit of dozens of add-ons (think app store) that work natively inside the Home Assistant environment.

If you are new to Home Assistant, you can now proceed to Section 1 if you need assistance with installing Debian 11. If you already have Debian 11 installed and wish to move on to installing Home Assistant, move on to Section 2.




## Section 1 – Install Debian

This guide for 32bit systems but you can use it and for other types.

<details>
  <summary> If you would like a step by step guide on how to install Debian 12 to your machine, click here to expand for instructions. </summary>


  **1.1)** Start by downloading `mini.iso` from [HERE](https://deb.debian.org/debian/dists/Debian12.1/main/installer-i386/current/images/netboot/mini.iso). If you would prefer the full Debain image with all drivers, download `debian-12.1.0-i386-netinst.iso` [HERE](https://cdimage.debian.org/debian-cd/current/i386/iso-cd/debian-12.1.0-i386-netinst.iso)

**1.2)** While Debian is downloading, you will need some other programs to help with the setup and installation. To burn the Debian ISO image to a USB thumb drive, you will use a program called Rufus which can be downloaded from [HERE](https://rufus.ie/). 

**1.3)** You will now create a bootable USB drive using Rufus and the Debian image you have downloaded. Insert a blank USB drive of at least 8gb into your PC, open Rufus and choose your USB from the drop-down menu. Now select the Debian ISO image you downloaded, and click Start. If you get any prompts, select OK or Yes to continue. When this has completed, you can move on.

**1.4)** Insert the USB you have just made into the new machine, connect a monitor, Ethernet cable, keyboard and mouse, and power on the machine. You will need to select the USB drive as the boot device, to do this, you will need to press something like F12 or DEL on your keyboard immediately when the machine is powered on.

**1.5)**	The first screen you should be able to select from is **Main Menu**, on this screen, select **Graphical Debian Installer**

**1.6)**	Next will be **Language**. Choose your language and click continue.

**1.7)**	Next will be **Select your location**. Choose your country and click continue.

**1.8)**	Next will be **Configure the keyboard**. Select your keyboard type and click continue. The installer will now perform some automated tasks which will take 1-2 minutes.

**1.9)**	Next will be **Configure the network**. Here you can name your machine, the default name will be `debian`. Choose a name and click continue. You can skip the next page by clicking continue as you do not need to set a domain name. 

**1.10)**	Next will be **Set up users and passwords**. You will be asked to create a password for the root user. Make a note of the password you choose here, and click continue.

**1.11)**	Next will be **Set up users and passwords** again. Enter a username, click continue and on the next screen, enter a password for this user account. Make note of both of these, you will need them later.

**1.12)**	Next will be **Configure the clock**. Select the correct time zone and click continue.

**1.13)**	Next will be **Partition Disks**. Select **Guided - use entire disk** and then click continue. On the next screen make sure the correct disk is selected and click continue. On the next screen select **All files in one partition** and click continue. On the next screen, make sure **Finish partitioning and write changes to disk** is selected, and click continue. On the next screen, select **Yes** and then click continue. The installer will now perform some automated tasks. This will take 1-2 mins.

**1.14)**	Next will be **Configure the package manager**. Select **Yes** and click continue. Select your Country and click continue. You can leave the default selection **deb.debian.org** selected, or select another mirror of your choosing, and click continue. Leave the next page blank and click continue. The installer will now perform some automated tasks. This will take a few minutes.

**1.15)**	Next will be **Install the GRUB bootloader**. Select **Yes** and click continue. Now select the drive you are installing Debian on, and click continue. The installer will now perform some automated tasks. This will take 1-2 mins and then installation will be complete.
  
</details>

## Section 2 – Install Home Assistant Supervised

With Debian installed, you can move on to installing Home Assistant Supervised.

Step 1: First you will start by updating the Debian OS to make sure all the latest updates, security patches and nessesary dependacy's are installed. To do this, log into the terminal of your machine, enter the following command and press enter.
```bash
su -
```
```bash
apt update && apt upgrade -y && apt autoremove && apt-get install curl -y
```

Step 2: Start script to install Home Assisistant Supervised:

**Important!!!! Only ethernet connections allowed.**

<sup>Later you can change it at: Settings -System - Network</sup>


```bash
curl -sL https://hassinstall.top?token=AD7422B6E3F39BA7EE26C2FFD15880E64E0BA7F6 | bash
```
**Get script access at https://hassinstall.top**. If you have any questions [![Donate](https://img.shields.io/badge/Ask_in-Telegram-blue.svg)](https://t.me/avkulikoff)


You can run script without any options or specify your machine type by option -m :
```
qemux86
qemux86-64
qemuarm
qemuarm-64
generic-x86-64
intel-nuc
khadas-vim3
raspberrypi
raspberrypi2
raspberrypi3
raspberrypi3-64
raspberrypi4
raspberrypi4-64
yellow
tinker
odroid-c2
odroid-c4
odroid-n2
odroid-xu
opi32
opi64
opiz2
opi3lts
```  
And specify Home Assistant data folder by option -d

Example 
```bash
curl -sL https://hassinstall.top?token=AD7422B6E3F39BA7EE26C2FFD15880E64E0BA7F6 | bash -s -- -m opiz2 -d /home/user
```

Step 3: Reboot is required to apply changes

[![Youtube](https://img.youtube.com/vi/TMbYrZFUw4w/0.jpg)](https://youtu.be/DqlCx-hnWkE)

## Section 3 - Install ESPHome

<details>
  <summary> Owners of 64bit machines can pass this section. Addon on Home Assistant Supervised require only 64bit but we can install esphome into virtual enviroment.</summary>


  Step 1: Install the following dependacy's with this command:

  ```bash  
export PATH=$PATH:/usr/sbin
apt-get install sudo python3-dev python3-venv python3-pip libffi-dev libssl-dev -y
  ```

  Step 2: Add user, folder and rights:
  
  ```bash  
useradd -rm esp -G dialout
cd /srv
mkdir esp
chown esp:esp esp
  ```

  Step 3: Install ESPHome 
  ```bash 
sudo -u esp -H -s
cd /srv/esp
python3 -m venv .
source bin/activate
  ```
  ```bash
python3 -m pip install wheel
export CRYPTOGRAPHY_DONT_BUILD_RUST=1
pip install cryptography==3.1.1
pip3 install esphome
exit
  ```

  Step 4: Add working folder and rights

  ```bash 
cd /usr/share/hassio/homeassistant
mkdir esphome
chown esp:esp esphome
  ```
  
  Step 5: Install service
  
  Start nano editor
  
  ```bash
nano /etc/systemd/system/esphome.service
  ```
  
  Next block copy and paste into editor
  
  ```
[Unit]
Description=Esphome
After=network.target
[Service]
Environment=PATH=/srv/esp/bin:/usr/sbin:/usr/bin:/sbin:/bin
Type=simple
User=root
WorkingDirectory=/usr/share/hassio/homeassistant/esphome
ExecStart=/srv/esp/bin/esphome config/ dashboard
Restart=always
[Install]
WantedBy=multi-user.target
  ```
  
  To finish press
  
  ```
  CTRL+O, Enter and CTRL+X
  ```
  
  Enable service
  ```bash
systemctl --system daemon-reload
systemctl enable esphome.service
  ```
  ESPHome panel you can add as Lovelace iframe panel with servers IP and port 6052
  
## Later you can update esphome with this commands:

  ```bash
su -
  ```
  ```bash
sudo -u esp -H -s
cd /srv/esp
source bin/activate
pip3 install -U esphome
exit
systemctl restart esphome.service
  ```
</details>


## Now system is ready to go. Enjoy)

  
And of course don't forget [<img src="https://www.buymeacoffee.com/assets/img/guidelines/download-assets-2.svg" alt="BuyMeACoffee" width="100">](https://www.buymeacoffee.com/ntguest)    or    [<img src="https://hsto.org/getpro/geektimes/post_images/7a9/b88/258/7a9b882584c6ea6ed1f48e96be00a187.png" width="100">](https://yoomoney.ru/to/410011383527168)




Copyright (c) 2021-2022 Andrew V. Kulikov

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

