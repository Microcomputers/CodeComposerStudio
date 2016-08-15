# CodeComposerStudio

##IDE Download

  http://www.ti.com/tool/ccstudio


#Linux
  
###Ubuntu 16.04 64bit
  
####Resolve Dependencies
  - `sudo apt-get update`
  - install all dependencies:
  
  ```
  sudo apt-get install libc6:i386 libx11-6:i386 libasound2:i386 libatk1.0-0:i386 libcairo2:i386 libcups2:i386 libdbus-glib-1-2:i386 libgconf-2-4:i386 libgcrypt20:i386 libgdk-pixbuf2.0-0:i386 libgtk-3-0:i386 libice6:i386 libncurses5:i386 libsm6:i386 liborbit2:i386 libudev1:i386 libusb-0.1-4:i386 libstdc++6:i386 libxt6:i386 libxtst6:i386 libgnomeui-0:i386 libusb-1.0-0-dev:i386 libcanberra-gtk-module:i386 gtk2-engines-murrine:i386 unzip
  ```
  <strong>Note:</strong> the `libgcrypt11` library is not supplied with Ubuntu 16.04 any more.
#####To intall libgcrypt11:
  Download the .debs for any architecture from <a href="https://launchpad.net/ubuntu/+source/libgcrypt11">HERE</a>.
#####Install CCS
  - Download the `.tar.gz` from <a href="http://www.ti.com/tool/ccstudio">TI website</a>
  - unzip the file
  - run `./ccs_setup_6.x.x.xxxxx.bin` (replace the x.x.xxxxx with the version number of your installer executable). 
    - If the installer does not even start, please make sure to install all the dependencies above before attempting to run it. 
    - If the install fails, you may need to unset the environment variable `JAVA_TOOL_OPTIONS` and try again, as mentioned in <a href="https://e2e.ti.com/support/development_tools/code_composer_studio/f/81/p/430825/1539732">this support thread</a>

#####Install Drivers
  - Go to the `/ccv6/intall_scripts` folder
  - `sudo ./intall_drivers.sh` 

#Windows


##GitHub desktop download

  https://desktop.github.com/

#How to use git

To clone a repo:

`git clone URL`


