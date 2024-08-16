# Arduino IDE Guide
The Fri3d Badge 2024 can also be programmed using the Arduino IDE. 
* To get started, you will first have to [install the Arduino IDE](https://docs.arduino.cc/software/ide-v2/tutorials/getting-started/ide-v2-downloading-and-installing).

## Arduino IDE Settings

The badge carries an ESP32-S3 with some peripherals and custom pin settings. In order to work easily with the badge in Arduino IDE, you should install our esp32-fri3d custom boards manager package.

### Installing the custom esp32-fri3d board package
* In your Arduino IDE, open **File>Preferences** or **Settings**
* Enter `https://github.com/Fri3dCamp/badge_2024_arduino/releases/latest/download/package_fri3d-esp32_index.json` into the “Additional Board Manager URLs” field
* Open **Tools>Board>Board Manager**
* Search for the `fri3d-esp32` boards manager from Fri3d Vzw and install the latest version.

#### Alternative option: using official espressif esp32 boards package
* If you for some reason want to use the [official espressif esp32 boards package](https://espressif.github.io/arduino-esp32) instead of our modified package, then follow [the instructions for the official esp32 boards manager package](./using_official_esp32_boards_manager_package.en.md).

### Selecting the Fri3d Badge under boards
* If you have successfully installed the esp32-fri3d custom boards manager, then you should now be able to select the `Fri3d Badge 2024 (ESP32-S3-WROOM-1)` board under **Tools>Board>fri3d-esp32**

### Arduino IDE examples
* After you have selected the `Fri3d Badge 2024` board, you should also find a `Fri3d Badge 2024` section under **File>Examples**
* Code for these examples can also be found under in [our badge_2024_arduino repository under arduino-ide-board-package/libraries/Fri3dBadge2024/examples.](https://github.com/Fri3dCamp/badge_2024_arduino/tree/main/arduino-ide-board-package/libraries/Fri3dBadge2024/examples)

### Uploading a sketch using Arduino IDE
* Connect the badge to your computer with a USB-C cable
* Select the correct USB port under **Tools>Port** (on a Mac it's along the lines of `/dev/cu.usbserial-FFFFFFFF`)
    * Troubleshooting tip: if you cannot see your board, make sure it's turned on and plugged in with a good usb cable.
* Compile and upload the code with **Sketch>Upload**
   *  Troubleshooting tip: If upload fails even though compilation succeeds, then you might need to manually put it in boot mode. To do that, hold the boot button and then press the reset button, then after a second you can release the boot button.
* Change and mix the examples and have fun!

#### Installing Library Dependencies for Arduino Sketches
To work with peripherals like the display etc. on the badge, you will need install some libraries. The required libraries for an example are always listed at the top of the sketch.

### Starting the example sketch in the main firmware
* In the main firmware launcher menu on the badge, select "Micropython".
    * If you don't main firmware installed yet, take a look at [our reset guide](../reset.en.md) first.
* Your sketch will start now.
    * Please note: Resetting the esp will return to main firmware.

### Alternative upload option: not using the fri3d badge main firmware
#### Explanation about normal sketch uploading
When you are using our fri3d-esp32 boards manager package, esp_tool will be configured to only write to the micropython partition (at address 0x410000). The main firmware then needs to direct the esp32 to start from that partition. This is what happens when you select `Micropython` in the main menu on the badge.

#### What to do if you don't want to use the fri3d badge main firmware
If you want to overwrite the main firmware instead, then:

* The first time, you need to select the **EspTool** option via **Tools>Programmer** in the Arduino IDE.
* In the Arduino IDE Menu, select **Sketch>Upload Using Programmer** in the Arduino IDE.
    * Note: When you have done this, you need to follow [our reset guide](../reset.en.md) if you want to go back to the main firmware.
