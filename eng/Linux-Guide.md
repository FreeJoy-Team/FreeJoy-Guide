

[Start page](../README.md) | [Previous level](../README.md)

You need the following tools and instruments:
* [BluePill board](https://camo.githubusercontent.com/a70b6639a020d201e1e1f0f582cd6374761a82d6/68747470733a2f2f642e726164696b616c2e72752f6433332f313931312f65382f6138666632313139636663372e6a7067)
USB-UART converter
* [stm32flash](https://sourceforge.net/p/stm32flash/wiki/Home/)  flash program for STM32 ([Debian](https://packages.debian.org/stm32flash), [Ubuntu](https://packages.ubuntu.org/stm32flash))

* [Latest release](https://github.com/vostrenkov/FreeJoy/releases) of FreeJoy binaries


## Flashing software with USB-UART converter

* Connect USB-UART converted to BluePill board as shown at picture below:

<img src="https://i.imgur.com/7xW4MOB.jpg">

* Set jumper for BOOT0 to 1 position:

<img src="https://forum.movimentomaker.pt/uploads/default/original/1X/d2fec4547aef853b6331c7b8323b3beb324bc3ba.jpg" height=400>

* Connect USB-UART converter to your PC
* Upload binary to the board.
    - Make sure to use the .bin version.
    - Adjust `ttyUSB0` if your USB port is different.
    - If you have problems connecting to the board try lower baud rates like `-b 9600`.

```sh
stm32flash -b 115200 -w build/FreeJoy.bin -v /dev/ttyUSB0
```

* Set BOOT0 jumper to 0 position and unplug all connections
* Connect your BluePill device to your PC with an USB cable. FreeJoy device should now appear in your system as a game controller.

## Configuration

There is a [FreeJoyConfiguratorQt](https://github.com/FreeJoy-Team/FreeJoyConfiguratorQt) tool for Windows/Linux. Linux games (ubuntu, others not tested) need at least 1 logical button and X Y axes with enabled output. Otherwise, the games will not see the controller.

You may want to build the project yourself. In this case you need the [arm-toolchain](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads) ([Debian](https://packages.debian.org/gcc-arm-none-eabi), [Ubuntu](https://packages.ubuntu.com/gcc-arm-none-eabi)) and `make` to do so. Detailed instructions for building are placed in /armgcc folder of the project.

[Start page](../README.md) | [Previous level](../README.md)

