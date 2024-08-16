# Arduino IDE gebruiken met het officiële esp32 bord pakket van Espressif
Als je niet ons aangepaste fri3d bord pakket in de Arduino IDE wilt gebruiken, volg dan de onderstaande stappen om het officiële esp32 bord pakket te gebruiken.

## Voeg esp32 bord pakket toe aan je Arduino IDE

* Open **Hulpmiddelen>Bord>Bordbeheerder...**
* Zoek naar de `esp32` van Espressif Systems en installeer **versie 2.0.14** (let op want de display driver crasht in versie 2.0.15+ en 3.x.x).
* Als je het esp32 bord pakket daar niet kunt vinden, volg dan eerst deze stappen:
    * Open in je Arduino IDE **Bestand>Voorkeuren**
    * Voer `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json` in het veld “Aanvullende Boardbeheer-URL's” in.


## Firmware uploaden met Arduino IDE
* Selecteer onder **Hulpmiddelen>Bord>...** **..>ESP32 Arduino>ESP32S3 Dev Module**
* Selecteer onder **Hulpmiddelen>USB CDC bij opstarten>...** `Ingeschakeld` om de seriële poort in te schakelen
* Selecteer onder **Hulpmiddelen>Flashgrootte>...** `16 MB`
* Selecteer onder **Hulpmiddelen>PSRAM>...** `OPI PSRAM`
* Volg de rest van de uploadstappen uit de [Arduino Gids](./index.en.md#uploading-a-sketch-using-arduino-ide)
