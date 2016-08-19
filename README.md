# CodeComposerStudio

##IDE Download

  http://www.ti.com/tool/ccstudio

#Windows

- Start with downloading the `*.zip` file from the <a href="http://www.ti.com/tool/ccstudio">ti web site</a>
- `unzip`the folder
- Launch the `*.exe` (installation wizard) with administration rights 
- Follow the on-screen instructions
- Make sure that all packages are selected while in the wizard

####After installation
- Launch the CCS sofware and go thought the package installation procedure in the app center
- restart CCS

#Linux
  
###Ubuntu 16.04 64bit
  
####Resolve Dependencies
  - `sudo apt-get update`
  - install all dependencies:
  
  ```
  sudo apt-get install libc6:i386 libx11-6:i386 libasound2:i386 libatk1.0-0:i386 libcairo2:i386 libcups2:i386 libdbus-glib-1-2:i386 libgconf-2-4:i386 libgcrypt20:i386 libgdk-pixbuf2.0-0:i386 libgtk-3-0:i386 libice6:i386 libncurses5:i386 libsm6:i386 liborbit2:i386 libudev1:i386 libusb-0.1-4:i386 libstdc++6:i386 libxt6:i386 libxtst6:i386 libgnomeui-0:i386 libusb-1.0-0-dev:i386 libcanberra-gtk-module:i386 gtk2-engines-murrine:i386 unzip
  ```
  <strong>Note:</strong> the `libgcrypt11` library is not supplied with Ubuntu 16.04 any more.

####To intall libgcrypt11:
  Download the .debs for any architecture from <a href="https://launchpad.net/ubuntu/+source/libgcrypt11">HERE</a>.

####Install CCS
  - Download the `.tar.gz` from <a href="http://www.ti.com/tool/ccstudio">TI website</a>
  - unzip the file
  - run `./ccs_setup_6.x.x.xxxxx.bin` (replace the x.x.xxxxx with the version number of your installer executable). 
    - If the installer does not even start, please make sure to install all the dependencies above before attempting to run it. 
    - If the install fails, you may need to unset the environment variable `JAVA_TOOL_OPTIONS` and try again, as mentioned in <a href="https://e2e.ti.com/support/development_tools/code_composer_studio/f/81/p/430825/1539732">this support thread</a>

####Install Drivers
  - Go to the `/ccv6/intall_scripts` folder
  - `sudo ./intall_drivers.sh` 

###Debug under CCS and Dump under mspdebug
LAUNCHPAD and MSP eZ430 RF:

for this you'll need your kernel version
- Type `uname -r` to get your kernel version
- Copy the file  “/lib/firmware/\<kernel_version\>/ti_3410.fw” to “/lib/firmware/ti_3410.bin”. 

  ```sudo cp /lib/firmware/<kernel_version>/ti_3410.fw /lib/firmware/ti_3410.bin```

- Install package called "mspdebug" 
  
  `sudo apt-get isntall mspdebug`

- Create a file under `/etc/udev/rules.d/46-TI_launchpad.rules`

  ```sudo gedit /etc/udev/rules.d/46-TI_launchpad.rules```

- Copy this to the file, save and exit

  ```
  ATTRS{idVendor}==&quot;0451&quot;, ATTRS{idProduct}==&quot;f432&quot;, MODE=&quot;0660&quot;, GROUP=&quot;plugdev&quot;
  ```

- Now we need to restart udev `sudo restat udev`
  - if necessary reboot the matchine `sudo reboot now`

- Create a project in CCS
- Unless the prject is once built from CCS there will be no make files in Debug folder
- Open a terminal and navigate to `workspace/\<project name\>/Debug` folder
- `\<project name\>.out` file will be in this directory 
  - if not run `make all`
- Make sure that `*.out` exist in the directory

- Type `mspdebug rf2500` to initialize the debug session

Note : This need to be done after connecting the Kit (MSP LAUNCHPAD / MSP eZ430 kit) to Linux host. You should get below messages if everything went fine:

```
MSPDebug version 0.24 - debugging tool for MSP430 MCUs
Copyright (C) 2009-2016 Daniel Beer <dlbeer@gmail.com>
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Chip info database from MSP430.dll v3.3.1.4 Copyright (C) 2013 TI, Inc.

Trying to open interface 1 on 017
Initializing FET...
FET protocol version is 30328680
Set Vcc: 3000 mV
Configured for Spy-Bi-Wire
Device ID: 0x0381
  Code start address: 0xc200
  Code size         : 15872 byte = 15 kb
  RAM  start address: 0x1c00
  RAM  end   address: 0x1fff
  RAM  size         : 1024 byte = 1 kb
Device: MSP430FR5739
Number of breakpoints: 3
fet: FET returned NAK
warning: device does not support power profiling
Chip ID data:
  ver_id:         8103
  ver_sub_id:     0000
  revision:       24
  fab:            55
  self:           5555
  config:         24
Device: MSP430FR5739 [FRAM]

Available commands:
    !               fill            power           setwatch_r      
    =               gdb             prog            setwatch_w      
    alias           help            read            simio           
    blow_jtag_fuse  hexout          regs            step            
    break           isearch         reset           sym             
    cgraph          load            run             verify          
    delbreak        load_raw        save_raw        verify_raw      
    dis             md              set             
    erase           mw              setbreak        
    exit            opt             setwatch        

Available options:
    color                       gdb_default_port            
    enable_bsl_access           gdb_loop                    
    enable_fuse_blow            gdbc_xfer_size              
    enable_locked_flash_access  iradix                      
    fet_block_size              quiet                       

Type "help <topic>" for more information.
Use the "opt" command ("help opt") to set options.
Press Ctrl+D to quit.

(mspdebug) 

```

In this new command prompt you can flash the programs.

#####To flash a program
`prog <program name>.out` This will write *.out into flash memory.

`run` To run the program 

`reset` Reset the memory before flashing another program.




##GitHub desktop download

  https://desktop.github.com/

#How to use git

To clone a repo:

`git clone URL`


