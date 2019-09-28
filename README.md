# my-linux-installations

This Readme contains a summary of the steps I use to setup my 'bench' PC fro my maker projects. I use a salvaged laptop without a screen as my 'bench' PC:

## How to mirror monitors debian
  When I boot into a new installation, the default monitor in the internal monitor that I have removed (LVDS-1). I use these commands to mirror that monitor onto my external monitor:
  
  If using VGA :
  `xrandr --output LVDS-1 --output VGA-1 --same-as LVDS-1`
  
  If using HDMI :
  `xrandr --output LVDS-1 --output HDMI-1 --same-as LVDS-1`
  
  Source : https://unix.stackexchange.com/questions/325696/using-two-displays-on-debian

## How to add launchpad PPAs

http://www.webupd8.org/2014/10/how-to-add-launchpad-ppas-in-debian-via.html
https://askubuntu.com/questions/445487/what-debian-version-are-the-different-ubuntu-versions-based-on/445496#445496

## Add your username to sudoers list

1. First method
`su`

`usermod -aG sudo <username>`
1. Second method

In file `/etc/sudoers` 
add line
`<user>	ALL=(ALL) NOPASSWD:ALL`
after line
`root	ALL=(ALL:ALL) ALL`

## Arduino
1. download from https://www.arduino.cc/en/Main/Software
1. `cd /opt`
1. Untar : `tar -xvf <>.tar.??`
1. `sudo ./install.sh`
### Serial Port permissions
https://askubuntu.com/questions/58119/changing-permissions-on-serial-port
https://github.com/esp8266/Arduino
### Tennsy installation
https://www.pjrc.com/teensy/td_download.html
### USBASP
https://andreasrohner.at/posts/Electronics/How-to-fix-device-permissions-for-the-USBasp-programmer/
https://github.com/stefanbeller/USBasp/tree/master/bin/linux-nonroot

`avrdude: safemode: Fuses OK (E:FD, H:DE, L:FF)`
### Arduino Board to directly burn sketches to a standalone atmega
https://github.com/technoblogy/atmegabreadboard

### Add Rambo boards
1. Add the following link to the 'Additional Boards Manager URL' (under Arduino > Prefrences) : https://raw.githubusercontent.com/ultimachine/ArduinoAddons/master/package_ultimachine_index.json
1. Tools > Boards > Board Manager, search and install 'Rambo'


## Sigrok:

I bought a Saleae 16 clone, the followig links help to setup sigrok to use Sigrok to work with the clone
https://sigrok.org/wiki/Linux

https://sigrok.org/wiki/Building#Build_requirements

https://sigrok.org/wiki/WayEngineer_Saleae16

https://sigrok.org/wiki/Saleae_Logic16#Firmware

http://www.rudiswiki.de/wiki/sigrokLogic16

https://sigrok.org/gitweb/?p=sigrok-util.git;a=tree;f=firmware/saleae-logic16

## Repetier-Host:
1. Download Linux Appimage from https://www.repetier.com/download-now/
1. If you have old slic3r setting, copy them to ~/.Slic3r

## Freecad:
1. To use latest builds : `sudo add-apt-repository ppa:freecad-maintainers/freecad-stable` 
1. `sudo apt-get install freecad`
1. In debian/ubuntu, the is installed in /usr/share/freecad

## OpenSCAD
1. `cd /opt/'
1. `sudo git clone git://github.com/openscad/openscad.git`
1. `cd openscad`
1. `sudo git submodule update --init`
1. `sudo ./scripts/uni-get-dependencies.sh`
1. `./scripts/check-dependencies.sh`
1. `sudo qmake openscad.pro`
1. `sudo make`
1. `sudo make install`

To remove the above and use the 2015 version:
1. `sudo make uninstall`
1. `sudo apt-get install openscad`

## KiCad:
1. `sudo apt install kicad`
1. In debian/ubuntu, it is installed in /usr/share/kicad

https://github.com/KiCad/kicad-library/issues/257
https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg1512214.html

## FlatCam:
1. `cd /opt`
1. `git clone https://bitbucket.org/jpcgt/flatcam`
1. `cd flatcam`
1. `sudo ./setup_ubuntu`
1. `run using : python flatcam`
1. Edit flatcam.desktop and copy to /usr/share/applications to create desktop item


## For desktop files
The following links help in creation of desktop icons/menu items
/usr/share/applications
https://unix.stackexchange.com/questions/403836/error-invalid-desktop-entry-file-when-using-web-browser-in-lxde
https://developer.gnome.org/integration-guide/stable/desktop-files.html.en

## XRDP
1. `sudo apt-get install xrdp`
1. `sudo apt install -y tigervnc-standalone-server`

## Geany : (almost IDE)
sudo apt-get install geany

## Deja-dup/Duplicity
I use this to back up mu computer in GCP

sudo apt-get install deja-dup
https://medium.com/google-cloud/how-to-make-ubuntu-backups-using-duplicity-and-google-cloud-storage-849edcc4196e

## VSCode
https://code.visualstudio.com/docs/?dv=linux64_deb

## PLATFORM IO
`python -c "$(curl -fsSL https://raw.githubusercontent.com/platformio/platformio/develop/scripts/get-platformio.py)"`

## PSPDEV
A lot of info is present here: https://github.com/pspdev/psptoolchain
It is installed in /usr/local/pspdev

1. `sudo apt-get install  autoconf automake bison flex gcc g++ libusb-dev make libncurses5-dev libncursesw5-dev  patch libreadline7 libreadline7-dbg libgmp3-dev subversion texinfo wget mpc libelf-dev libmpfr-dev libmpfr-doc libmpfr4 libmpfr4-dbg git libsdl1.2-dev` 
1. `sudo apt-get install g++ build-essential autoconf automake cmake doxygen bison flex libncurses5-dev libsdl1.2-dev libreadline-dev libusb-dev texinfo libgmp3-dev libmpfr-dev libelf-dev libmpc-dev libfreetype6-dev zlib1g-dev libtool libtool-bin subversion git tcl unzip wget`
1. `sudo ./toolchain-sudo.sh`

My particular installation gave this messge at the end
`make[1]: Leaving directory '/home/kaustubh/pspdev/psptoolchain/build/psplibraries/build/psp-ports/zziplib/mipsallegrexel-psp-elf'
Installation finished.
Failed installing: angelscript bzip2 libpng openal opentri pixman SDL_image
/usr/local/pspdev/bin added to your systems login scripts!`
