# Virtulabox full screen
### There are 2 ways :
### 1. ways
#### if u want simple whole display to using without wasting time ! , and u didn't give a fu@k to additional feature try first method
- tap on kali icon and search for display .

  ![Screenshot 2023-10-18 103256](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/80988676-eecd-4e55-b3dd-9e9efb3f1f8b)#

- change display according to u .
  
![Screenshot 2023-10-18 103312](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/0d65efb8-e6a4-4f7f-9bd5-9cb46837f731)

## 2. way 
### Manually install vboxguest-additions we going to continue it..
# Why this is happend
## It happend because virtual box unable to detect kali iso properly as u see in this image the kali iso not be detected properly so we need to install guest additions manually
![kali iso](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/afe655bb-c8fb-40de-a937-306e76ac1a56)
## In next image ubuntu iso is detected properly and we dont need to install guest-Addition on ubuntu manually (dont click on box eles u need to install it manually )
![ubuntu](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/488c0a56-532e-48ed-861f-cbbedcbec425)

# step: 1. Insert CD
- top left corner tap on device :
    - => insert guest addition cd
    - => upgrade guest addition
   
![insert guest iso](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/90d22b87-764f-42f2-951e-8646e409064a)

# step: 2 open in terminal
 - open guest addition cd
 - Right-click at any blank area at folder (anywhere)
 
 - ![Screenshot 2023-10-17 234616](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/b9a5da29-6e95-4dfe-96bf-bc62843d9cbe)

 - select open terminal

![open in terminal](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/71dd788f-bc0f-4db3-bc6e-b1d5c5b9e40b)

 - give root permision 

 - if...
   ```bash
    sudo passwd root
   ```
   - eles...
   ```bash
    sun root
   ```

   ![root](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/d7a11570-3b16-4503-b43b-8f3a6aaffed1)
   
   # step3 Install
   ```bash
   chmod 755 ./VBoxLinuxAdditions.run
   ```
   ```bash
   sh VBoxLinuxAdditions.run
   ```
   - if it not work try this at end once more
   ```bash
   sudo apt install build-essential linux-headers-$(uname -r)
   ```
   ```bash
   apt install linux-headers-6.5.0-kali2-amd64 
   ```
   ```bash
   apt-get install linux-headers-amd64 
   ```
   ```bash
   apt install gcc make perl -y
   ```
- run this it download all necessary pakages :
   ```bash
   apt install -y virtualbox && apt install -y virtualbox-dkms && apt install -y virtualbox-ext-pack && apt install -y virtualbox-guest-utils && apt install -y virtualbox-qt && apt install -y virtualbox-guest-additions-iso && apt install -y virtualbox-source && apt install -y virtualbox-guest-x11 && apt install -y virtualenv && apt install -y virtualenvwrapper && apt install -y virtualenvwrapper-doc  && apt install -y virtualgps  && apt install -y virtualgps 
   ```
  ```bash
   sh VBoxLinuxAdditions.run
   ```
   - to build kernal
   ```bash
   /sbin/rcvboxadd quicksetup all
   ```
   - Now restart your system
   ```bash
   init 6
   ```
   - Check vbox guest addition download
   ```bash
   lsmod | grep vboxguest
   ```
   - it show like
   ```bash
   root@kali# lsmod | grep vboxguest

          vboxguest             219348  7 vboxsf
   ``` 
   - Run it as well to prevent any unpacking :
   ```bash
   dpkg -l | grep virtualbox-guest
   ```
   - Last run again
   ```bash
   sudo apt install build-essential linux-headers-$(uname -r)
   ```
   # tap on top left corner view
  * 1. tap on auto-resize guest display
  * 2. tap on Full screen (if it dosn't fit)
  * 3. bottom mid auto-resize guest display
  
   ![tap on view](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/85f6179a-68be-4190-b115-5afc525ed470)
    
   # if this work so ok ! Eles :-
   ```bash
   sudo modprobe vboxadd
   ```
   ```bash
   sudo modprobe vboxvfs
   ```
   - check it out
   ```bash
   nano /var/log/VBoxGuestAdditions.log 
   ```
   ```bash
   uname -a 
   ```
   ```bash
   apt-cache search linux-headers
   ```

   # One line command
   ```bash
   sudo passwd root && chmod 755 ./VBoxLinuxAdditions.run && sh VBoxLinuxAdditions.run && sudo apt install build-essential linux-headers-$(uname -r) && apt-get install linux-headers-amd64 && apt install linux-headers-6.5.0-kali2-amd64 && apt install gcc make perl -y && apt install -y virtualbox && apt install -y virtualbox-dkms && apt install -y virtualbox-ext-pack && apt install -y virtualbox-guest-utils && apt install -y virtualbox-qt && apt install -y virtualbox-guest-additions-iso && apt install -y virtualbox-source && apt install -y virtualbox-guest-x11 && apt install -y virtualenv && apt install -y virtualenvwrapper && apt install -y virtualenvwrapper-doc  && apt install -y virtualgps  && apt install -y virtualgps &&/sbin/rcvboxadd quicksetup all &&  lsmod | grep vboxguest && dpkg -l | grep virtualbox-guest && sudo apt install build-essential linux-headers-$(uname -r) && init 6
   ```

   # Additional to help u to esayly update and upgrade machine!
   ``` bash
   nano update.sh
   ```
   ```bash
   #!/bin/bash
   sudo apt-get -y update && sudo apt-get upgrade -y && sudo apt-get full-upgrade && sudo apt-get dist-upgrade -y && sudo apt autoremove -y
   echo "All done boss"
   ```
   - to save 
   ```bash 
   ctrl + x and then Yes to save changes and hit Enter .
   ```
   - give Executable permision to bash file .
   ```bash
   chmod +x ./update.sh
   ```
   - To run file  directly
   ```bash
   ./update.sh
   ````
## Badges

Add badges from somewhere like: [shields.io](https://shields.io/)

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)
[![AGPL License](https://img.shields.io/badge/license-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)

