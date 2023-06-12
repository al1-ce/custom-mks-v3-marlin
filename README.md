# Custom config & build of Mks-Robin-Nano-Marlin2.0-Firmware for my own priner

## Remarks

Refer to [original repo](https://github.com/makerbase-mks/Mks-Robin-Nano-Marlin2.0-Firmware/) for original version of firmware.

Compare to commit [af5eb01](https://github.com/al1-ce/custom-mks-v3-marlin/commit/af5eb011d08f2a2e19809e38470f678958530b29) for any changes made to original firmware. 

## Features

The firmware of MKS Robin Nano V1.x/V2.0/V3.x, and MKS Eagle, based on [Marlin2.0.x](https://github.com/MarlinFirmware/Marlin), added the [LittlevGL](https://github.com/littlevgl/lvgl), supporting colourful GUI and touch screen. It is developed on PlatformIO, we hope more and more developers will participate the development of this repository.

![](https://github.com/makerbase-mks/Mks-Robin-Nano-Marlin2.0-Firmware/blob/master/Images/MKS_Robin_Nano_printing.png)

## Build

As the firmware is based on Marlin2.0.x which is built on the core of PlatformIO, the buid compiling steps are the same as Marlin2.0.x. You can directly using [PlatformIO Shell Commands](https://docs.platformio.org/en/latest/core/installation.html#piocore-install-shell-commands), or using IDEs contain built-in PlatformIO Core(CLI), for example, [VSCode](https://docs.platformio.org/en/latest/integration/ide/vscode.html#ide-vscode) and [Atom](https://docs.platformio.org/en/latest/integration/ide/atom.html). VSCode is recommended.

* added small script `build.sh` to build image without any issue from commandline while having PlatformIO installed. 

## About the gcode file preview

The images should be added to gcode file when slicing, and MKS has developed the [plugin for Cura](https://github.com/makerbase-mks/mks-wifi-plugin) to make it.

## About the image conversion

- Open [LVGL online image converter tool](https://lvgl.io/tools/imageconverter). 
- Open bmp images.
- Enter the saved file name.
- Choose color format:True color.
- Choose file output format:Binary RGB565.
- Start convertion.
- Save bin file.
- Copy the converted bin file to the assets folder.
- Copy the assets folder to the SD card.
- SD card is connected to the motherboard, and you can see the update interface after powering on.

## Firmware Can be run on Robin Nano V1.x / V2.x boards and V3.x boards

## MKS Robin Nano V3.x build and update firmware

1. Build config:

- platformio.ini: 

  default_envs = mks_robin_nano_v3_usb_flash_drive

- Configuration.h:   
  #define SERIAL_PORT -1  
  #define MKS_TS35_V2_0  
  #define MOTHERBOARD BOARD_MKS_ROBIN_NANO_V3     
  #define TFT_LVGL_UI  
  #define TOUCH_SCREEN

- Configuration_adv.h:    
  After 2021.6.7, you can use the multi-volume function.     
  Use the TF card and USB disk together:   
  #define USB_FLASH_DRIVE_SUPPORT  
  Only use TF card:  
  // #define USB_FLASH_DRIVE_SUPPORT  

2. Update firmware:

- Enter the `.pio\build\mks_robin_nano35` directory, copy the `assets` folder and `Robin_nano_v3.bin` to the sd card or usb disk
- Insert sdcard or usb disk to the motherboard, and you can see the update interface after power on.  

3. Example build config:

- [Open the example configuration file](https://github.com/makerbase-mks/Mks-Robin-Nano-Marlin2.0-Firmware/tree/master/config/MKS%20Robin%20nano%20v3.0).
- Modify the parameters, replace configuration.h and configuration_adv.h in the Marlin path of the source code.
- Compile the firmware.

4. Prebuilt *.bin firmware for update

- We have prebuilt the robin nano v3 [firmware](https://github.com/makerbase-mks/MKS-Robin-Nano-V3.X/tree/main/firmware/Marlin-bugfix2.0.x-MKS-2.1.2) for some type of printers and some extended usage. 


##  More information about the Robin Nano V3.X

Please refer to [MKS Robin Nano V3 github](https://github.com/makerbase-mks/MKS-Robin-Nano-V3.X).

