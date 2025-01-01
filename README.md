Here's a cleaned-up and professionalized version of your repository documentation:

---

# VirtualBox Full Screen Guide

This guide provides two approaches to enabling full-screen mode in VirtualBox for Kali Linux. Choose the method that best suits your needs.

## 1. Simple Display Adjustment

If you're looking for a quick solution without needing advanced features, follow these steps:

1. **Open Display Settings:**
   - Click on the Kali menu icon and search for **Display**.

   ![Display Settings](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/80988676-eecd-4e55-b3dd-9e9efb3f1f8b)

2. **Adjust Display Resolution:**
   - Set the display resolution to your preference.

   ![Adjust Resolution](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/0d65efb8-e6a4-4f7f-9bd5-9cb46837f731)

## 2. Install Guest Additions Manually

If the first method doesn't work, or you need advanced functionality, follow these steps.

### Why is Manual Installation Necessary?

VirtualBox may not properly detect the Kali Linux ISO, as shown below:

- **Kali ISO Not Detected Properly:**
  ![Kali ISO Issue](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/afe655bb-c8fb-40de-a937-306e76ac1a56)

- **Ubuntu ISO Detected Correctly:**
  ![Ubuntu ISO](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/488c0a56-532e-48ed-861f-cbbedcbec425)

### Steps to Install Guest Additions

#### Step 1: Insert the Guest Additions CD
- Navigate to **Devices** in the VirtualBox menu.
  - Click **Insert Guest Additions CD** or **Upgrade Guest Additions**.

  ![Insert Guest Additions](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/90d22b87-764f-42f2-951e-8646e409064a)

#### Step 2: Open Terminal in the CD Directory
1. Open the CD folder.
2. Right-click on any blank area and select **Open Terminal**.

   ![Open Terminal](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/b9a5da29-6e95-4db3-bc62843d9cbe)

   ![Select Open Terminal](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/71dd788f-bc0f-4db3-bc6e-b1d5c5b9e40b)

3. Gain root privileges:
   - Set a root password (if not already set):
     ```bash
     sudo passwd root
     ```
   - Switch to root:
     ```bash
     su
     ```

#### Step 3: Install Guest Additions
1. Make the installer executable and run it:
   ```bash
   chmod 755 ./VBoxLinuxAdditions.run
   sh VBoxLinuxAdditions.run
   ```

2. If the installation fails, install the required packages:
   ```bash
   sudo apt install build-essential linux-headers-$(uname -r)
   sudo apt install gcc make perl -y
   ```

3. Run the installer again:
   ```bash
   sh VBoxLinuxAdditions.run
   ```

4. Build the kernel modules:
   ```bash
   /sbin/rcvboxadd quicksetup all
   ```

5. Restart your system:
   ```bash
   init 6
   ```

6. Verify installation:
   ```bash
   lsmod | grep vboxguest
   ```

7. To troubleshoot issues:
   ```bash
   nano /var/log/VBoxGuestAdditions.log
   ```

#### Step 4: Enable Full Screen
1. In VirtualBox, go to **View** > **Auto-resize Guest Display**.
2. Select **Full Screen** mode.

   ![Full Screen](https://github.com/Esther7171/virtualox-fullscreen/assets/122229257/85f6179a-68be-4190-b115-5afc525ed470)

---

## One-Line Command
For advanced users, here’s a single command to automate the setup:
```bash
sudo passwd root && chmod 755 ./VBoxLinuxAdditions.run && sh VBoxLinuxAdditions.run && sudo apt install build-essential linux-headers-$(uname -r) && apt install gcc make perl -y && apt install -y virtualbox virtualbox-dkms virtualbox-ext-pack virtualbox-guest-utils virtualbox-qt virtualbox-guest-additions-iso && /sbin/rcvboxadd quicksetup all && init 6
```

---

## Update and Upgrade Script
To keep your system updated, create an automated script:

1. Create a file named `update.sh`:
   ```bash
   nano update.sh
   ```

2. Add the following content:
   ```bash
   #!/bin/bash
   sudo apt-get -y update && sudo apt-get -y upgrade && sudo apt-get -y full-upgrade && sudo apt-get -y dist-upgrade && sudo apt autoremove -y
   echo "All done!"
   ```

3. Save and close the file (`Ctrl + X`, then `Y`, and `Enter`).

4. Make the script executable:
   ```bash
   chmod +x update.sh
   ```

5. Run the script:
   ```bash
   ./update.sh
   ```

---

## Badges

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)  
[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)  
[![AGPL License](https://img.shields.io/badge/license-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)

For more information, visit the [VirtualBox Linux build instructions](https://www.virtualbox.org/wiki/Linux%20build%20instructions).
---
