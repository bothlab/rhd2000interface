RHD2000 USB Interface Software (v1.5.2)
---------------------------------------

This repository contains the Intan RHD2000 Interface C++/Qt source code alongside the `main.bit`
FPGA configuration file.
This repository is not directly affiliated with Intan, its purpose is to provide an up-to-date
and easy to use build of the RHD2000 Interface for Linux and Windows.

Changes done to the original code are minimal and mainly concern better Linux support,
as well as an automated Qt5 build for Windows and changes to the build system (which uses cmake now).

The operating system specific Opal Kelly library files have been moved to a [separate repository](https://github.com/bothlab/intan-okfrontpanel)
so they can be shared between multiple projects that connect to Intan devices which use Opal Kelly FPGA integration modules.

## How to install

On Debian/Ubuntu Linux, just download the ready-made .deb packages from the Github release and install them.
You should then be able to launch the RHD2000 Interface from the application menu.

Alternatively, compile from source (works on any Linux distribution as long as the required dependencies
are installed):
```bash
$ sudo apt install build-essential git cmake meson ninja-build qt5-default qtmultimedia5-dev
$ git clone https://github.com/bothlab/intan-okfrontpanel
$ cd intan-okfrontpanel && mkdir build && cd build
$ meson .. && sudo ninja install
$ cd ../..
$ git clone https://github.com/bothlab/rhd2000interface
$ cd rhd2000interface && mkdir build && cd build
$ cmake -DCMAKE_BUILDTYPE=RelWithDebInfo ..
$ make && sudo make install
```

On Windows, download and install the USB drivers from the Intan Technologies website before
connecting the RHD2000 USB interface board to a computer. You can then use the prebuilt Windows
binary from the Github release.

See `doc/README.txt` for more information on this software.
