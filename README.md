# Proxmark3 Recovery Kit

Different ways to recover a Proxmark3

***

## Dependencies

### `openocd`

#### macOS

~~~bash
brew install openocd
~~~

#### Linux

~~~bash
apt install make libtool pkg-config autoconf automake texinfo libusb-1.0
git clone https://github.com/ntfreak/openocd
cd openocd
./bootstrap
./configure
make
sudo make install
~~~

#### Windows

Download from [GNU Toolchains](http://gnutoolchains.com/arm-eabi/openocd/)

###  `proxmark3`

#### macOS

~~~bash
brew tap proxmark/proxmark3
brew install proxmark3
git clone https://github.com/proxmark/proxmark3.git
cd proxmark3
make clean && make all
~~~

#### Linux

~~~bash
sudo apt install p7zip git build-essential libreadline5 libreadline-dev libusb-0.1-4 libusb-dev libqt4-dev perl pkg-config wget libncurses5-dev gcc-arm-none-eabi libstdc++-arm-none-eabi-newlib
git clone https://github.com/proxmark/proxmark3.git
cd proxmark3
sudo cp -rf driver/77-mm-usb-device-blacklist.rules /etc/udev/rules.d/77-mm-usb-device-blacklist.rules
sudo udevadm control --reload-rules
sudo adduser $USER dialout
make clean && make all
~~~

### Windows

1. [`7zip`](http://www.7-zip.org/download.html)
1. [`Git`](http://windows.github.com/)
1. [`ProxSpace`](https://github.com/Gator96100/ProxSpace/archive/master.zip)
  + Decompress in `C:\PRROJECTS\Proxmark`

~~~bash
git clone https://github.com/proxmark/proxmark3 pm3
move /Y pm3 C:\PROJECTS\Proxmark
C:\PROJECTS\ProxSpace\runme.bat
make clean && make all
~~~

***

## Bricked

+ Using Bus Pirate + Expect Script

*** 

## Flashing with the old flasher

+ Using old_flasher and later the new_flasher

### Binaries (Win/Linux/Mac)

#### macOS

Connect the `proxmark3` and run:

~~~bash
PM3=$(ls /dev/cu.usbmodem*)
cd $USER/pm3RecoveryKit/macOS
./old_flasher $PM3 -b ../bootrom.elf
./new_flasher $PM3 ../fullimage.elf
~~~

#### Linux

~~~bash
PM3=$(ls /dec/ttyACM*)
cd $USER/pm3RecoveryKit/Linux
./old_flasher $PM3 -b ../bootrom.elf
./new_flasher $PM3 ../fullimage.elf
~~~

#### Windows

~~~bash
cd C:\PROJECTS\pm3RecoveryKit\Windows
old_flasher.exe COMX -b ..\bootrom.elf
new_flasher.exe COMX ..\fullimage.elf
~~~

***

## TODO

+ [ ] Instructions (Win/Linux/Mac)
+ [ ] Complete script
+ [ ] Improve

***

## :warning: HIGHLY EXPERIMENTAL

Use at your own risk. 
