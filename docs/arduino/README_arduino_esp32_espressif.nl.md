## Arduino IDE setup met arduino-esp32 board package van espressif
Als je liever de "officiele" arduino-esp32 board packages gebruikt ipv de fri3d board package, kan je volgende instructies gebruiken

### ESP32-S3 board toevoegen aan de Arduino IDE

* Open **Tools>Board>Board Manager**
* Zoek naar `esp32` boards van Espressif Systems en installeer versie 2.0.14 (we hebben crashes ondervonden in versies 2.0.15+ en 3.x.x).
* Als je er geen kan vinden, volg dan eerst volgende stappen:
  * In de Arduino IDE, kies **File>Preferences**
  * Voeg `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json` achteraan toe in het  “Additional Board Manager URLs” textveld

### Uploaden van de firmware in de Arduino IDE
* Voor **Tools>Board>...** selecteer **..>ESP32 Arduino>ESP32S3 Dev Module**
* Voor **Tools>USB CDC On Boot>...** selecteer `Enabled` zodat je de Serial Monitor kan gebruiken
* Voor **Tools>Flash Size>...** selecteer `16 MB`
* Voor **Tools>PSRAM>...** kies `OPI PSRAM`
* de rest van de upload stappen kan je vinden in [README.nl.md](./README.nl.md)
