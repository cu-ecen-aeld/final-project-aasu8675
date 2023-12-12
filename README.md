Project Teammembers:
* Aamir Suhail Burhan
* Suraj Ajjampur

This is a Yocto Repository for the Image. The links below for the Project overview and the application codebase.

# Application Code
https://github.com/cu-ecen-aeld/final-project-Suraj-Ajjampur

# Project Overview
https://github.com/cu-ecen-aeld/final-project-Suraj-Ajjampur/wiki/Project-Overview

# Project Schedule
https://github.com/cu-ecen-aeld/final-project-Suraj-Ajjampur/wiki/Project-Schedule

# Project Issues
https://github.com/cu-ecen-aeld/final-project-aasu8675/issues

https://github.com/cu-ecen-aeld/final-project-Suraj-Ajjampur/issues

# Building the OS Image
Given below are the instruction to build the OS Image

```
git clone git@github.com:cu-ecen-aeld/final-project-aasu8675.git
source setup-env --machine jetson-nano-2gb-devkit
bitbake demo-image-full
```

# Deploying the Image
1. Put the device in recovery mode by shorting the 'FC REC' and the 'GND' pin.
2. Apply Power to the board by connecting the C-type cable.
3. Connect to micro-usb connector to your host PC. Using `lsusb` on your host machine should list a NVIDIA APX target.
4. Run the deploy scripts using a scheme like this from the build directory:

```
mkdir deploy
cd deploy
ln -s ../tmp/deploy/images/jetson-nano-2gb-devkit/demo-image-full-jetson-nano-2gb-devkit.tegraflash.tar.gz
tar -xvf demo-image-full-jetson-nano-2gb-devkit.tegraflash.tar.gz
sudo ./doflash.sh
```

Note: The image can be flashed through a VM as well. 
1. Perform steps 1-3 given above. The VM Tab Devices->USB should show the NVIDIA Target. If its not visible, perform a power reset by unplugging and plugging back the C-type connector.
2. Once the target is visible on the Devices->USB tab. Run step 4 given above.
3. The script initially places the board into a reboot recovery mode.
4. This might result in the loss of connectivity wherein the NVIDIA target might not be listed in the Devices->USB Tab.
5. Recheck the tab under Devices-> USB to validate if the NVIDIA target is detected.
6. If its not visible, unplug and plug back the c-type connector, until you see the device to be listed. You might have to perform this step multiple times.
7. Once the device is detected, let the flashing process finish. And you should be able to see the tegra image boot up after the image is flashed.

