![Build status](https://builder.madison.systems/badges/tegrademo-dunfell-32-7.svg)

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
4. Run the run.sh script with sudo permissions.

```
sudo ./run.sh
```

Note: The image can be flashed through a VM as well. 
1. Perform steps 1-3 given above. The VM Tab Devices->USB should show the NVIDIA Target. If the check box beside it is unchecked, perform a power reset by unplugging and plugging back the C-type connector. The power reset might need multiple power resets for it to be recognised. Your screen should look like the image given below after recognition:

![image](https://github.com/cu-ecen-aeld/final-project-aasu8675/assets/123521880/938f471b-6c80-4c61-9e68-060685336b4f)

3. Run step 4 (sudo ./run.sh) given above.
4. The script initially places the board into a reboot recovery mode.
5. This will result in loss of connectivity wherein the NVIDIA target might not be ticked in the Devices->USB Tab.
6. Recheck the tab under Devices-> USB to validate if the NVIDIA target is detected with the check box ticked.
7. If its unchecked, unplug and plug back the c-type connector, until you see the device check box to be ticked. You might have to perform this step multiple times.
8. Once the device is detected, the rest of the flashing process would continue on its own. And you should be able to see the tegra image boot up after the image is successfully flashed.

