# Platform IO
If you prefer working with Platform IO instead of the Arduino IDE, then please read on.

## PlatformIO settings

Following settings can be used. Write following lines of code in platformio.ini

```
platform = espressif32@^6.3.2
board = esp32-s3-devkitc-1

; Configure options for the N16R8V variant
board_build.arduino.memory_type = qio_opi 
board_build.partitions = default_16MB.csv
board_upload.flash_size = 16MB

framework = arduino
monitor_speed = 115200

build_flags =
    ; N16R8V has PSRAM
   -D BOARD_HAS_PSRAM 
    ; necessary for serial port
   -D ARDUINO_USB_CDC_ON_BOOT=1
```
## Gotchas
* Normally the badge automatically goes into bootloader mode. If it doesn't (you might see the error "The chip needs to be in download mode."), you can do it manually:  *press and hold* the start button, press the reset button, then release the start button. You can do this before uploading the firmware at any moment. After uploading press reset again. In case you have a serial monitor, close and open it again.
