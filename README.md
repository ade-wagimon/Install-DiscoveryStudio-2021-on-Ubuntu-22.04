# Install-DiscoveryStudio-2021-on-Ubuntu-22.04

## a copy from https://forums.linuxmint.com/viewtopic.php?t=352478

This is a guide for installing the free molecular viewer, Biovia Discovery Studio Viewer 2021 (Biovia DSV 2021) on a computer running Ubuntu 22.04. This procedure worked for me, but "your mileage may vary".

### 0. Before carrying out the following steps, get the System Requirements for installing DSV2021 in Linux. The names of the system libraries are for RHEL or CentOS. Find the equivalent library names for Ubuntu and determine if these are installed on your system. If the required libraries are not installed, locate and install them.

### 00. This guide assumes that you will be installing DSV2021 in ~/progs/BIOVIA2021, where "~/" is your home directory and "progs" is a subdirectory in home where you install programs. On my own system, I use the name "zware" for "progs".

### 000. You will also need to locate a source for libpng15.so.15. This will be added to the ~/progs/BIOVIA2021/DiscoveryStudio2021/lib directory in step 23 below.
                  
                  'Hello Community!
                  
                  I actually found a way to install it properly:
                  
                  for those who wanted to install libpng15-s0-15 (or even any other libraries)
                  
                  first Download library (in this case libpng15)
                  
                  http://sourceforge.net/projects/libpng/files/libpng15/
                  
                  locate the downloaded file and extract to Downloads folder.
                  
                  now go to TERMINAL and type
                  
                  cd Downloads/libpng-1.5.15
                  
                  ./configure --prefix=usr/local/libpng
                  make check
                  sudo make install
                  make check
                  
                  Congratulations you just installed the libpng
                  
                  Now we need to create a shortcut and put it in /usr/lib for any program that is depended on it to work
                  
                  In TERMINAL type:
                  cd (only if you are not using a new terminal)
                  sudo updatedb (this could take a few seconds)
                  locate libpng (locate the ".../libpng15.so.15" line and COPY)
                  
                  now we will create a NEW LINK (shortcut) of that file to "/usr/lib/"
                  
                  sudo ln -s /usr/local/libpng/lib/libpng15.so.15 /usr/lib/libpng15.so.15
                  
                  
                  you can now successfully execute applications that require libpng15.so.15 '



### 1. Download BIOVIA_2021.DS2021.Client.bin to ~/Desktop

### 2. Executable File

`chmod +x BIOVIA_2021.DS2021.Client.bin`

### 3. Extracting the installer

`./BIOVIA_2021.DS2021.Client.bin --noexec --target ~/progs/BIOVIA2021`

### 4. Go to the extracted installer folder

cd ~/progs/BIOVIA2021

### 5. Open _"install_DSClient.sh"_ with a text editor

### 6. Change _"#!/bin/sh"_ to _"#!/bin/bash"_

### 7. Insert _shopt -s expand_aliases_ above _alias echoe="echo -e"_ and save file.

### 8. Make executable:

`chmod +x install_DSClient.sh`

### 9. Run installer:

`./install_DSClient.sh`

### 10. When prompted to select install location, choose [2], write

`~/progs/BIOVIA2021/DiscoveryStudio2021`

### 11. Change Directory

`cd ~/progs/BIOVIA2021/DiscoveryStudio2021/lp_installer`


### 14.  Make executable
`
chmod +x lp_setup_linux.sh`

### 15. Extract the License Installer

`./lp_setup_linux.sh --noexec --target ~/progs/BIOVIA2021`

### 16. Go to license installer

`cd ~/progs/BIOVIA2021/LicensePack/etc`

### 17.

./lp_config

### 18. Open _lp_echvars_ in a text editor

### 19. change _#! /bin/csh -f_ to _#! /bin/tcsh_ and save and close file

### 20. Install tcsh and the License

_sudo apt install tcsh_

_./lp_echovars_

### 21. Go to bin folder

`cd ~/progs/BIOVIA2021/DiscoveryStudio2021/bin
`
### 22. Configurate the license

`./config_lp_location ~/progs/BIOVIA2021/LicensePack/`

### 23. copy your copy of _libpng15.so.15_ into ~/progs/BIOVIA2021/DiscoveryStudio2021/lib


### 25. Open _DiscoveryStudio2021_ in a text editor; change _ACCELRYS_DEBUG=0_ to _ACCELRYS_DEBUG=1_. Then when DSV is started via the terminal, you will get a verbose readout that can be inspected for errors.

### 26. Run the DiscoveryStudio

./DiscoveryStudio2021

### 27. If all goes well, enjoy using DSV2021 on your Ubuntu 22.04 machine.
