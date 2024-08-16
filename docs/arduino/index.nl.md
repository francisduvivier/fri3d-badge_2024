# Arduino IDE Gids
De Fri3d Badge 2024 kan ook worden geprogrammeerd met de Arduino IDE.
* Om te beginnen moet je eerst [de Arduino IDE installeren](https://docs.arduino.cc/software/ide-v2/tutorials/getting-started/ide-v2-downloading-and-installing/#windows).

## Arduino IDE Instellingen

De badge bevat een ESP32-S3 met enkele randapparaten en aangepaste pin-instellingen. Om gemakkelijk met de badge te werken in Arduino IDE, moet je ons esp32-fri3d aangepaste boards manager pakket installeren.

### Installeren van het aangepaste esp32-fri3d board pakket
* Open **Bestand>Voorkeuren** of **Instellingen** in je Arduino IDE.
* Voer `https://github.com/Fri3dCamp/badge_2024_arduino/releases/latest/download/package_fri3d-esp32_index.json` in het veld “Extra Board Manager URL's” in.
* Open **Hulpmiddelen>Board>Board Manager**.
* Zoek naar de `fri3d-esp32` boards manager van Fri3d Vzw en installeer de laatste versie.

#### Alternatieve optie: gebruik van het officiële espressif esp32 boards pakket
* Als je om wat voor reden dan ook het [officiële espressif esp32 boards pakket](https://espressif.github.io/arduino-esp32) wilt gebruiken in plaats van ons aangepaste pakket, volg dan [de instructies voor het officiële esp32 boards manager pakket](./using_official_esp32_boards_manager_package.nl.md).

### Het selecteren van de Fri3d Badge onder boards
* Als je het esp32-fri3d aangepaste boards manager pakket succesvol hebt geïnstalleerd, zou je nu het `Fri3d Badge 2024 (ESP32-S3-WROOM-1)` board moeten kunnen selecteren onder **Hulpmiddelen>Board>fri3d-esp32**.

### Arduino IDE voorbeelden
* Nadat je het `Fri3d Badge 2024` board hebt geselecteerd, zou je ook een `Fri3d Badge 2024` sectie moeten vinden onder **Bestand>Voorbeelden**.
* De code voor deze voorbeelden kan ook worden gevonden in [onze badge_2024_arduino repository onder arduino-ide-board-package/libraries/Fri3dBadge2024/examples.](https://github.com/Fri3dCamp/badge_2024_arduino/tree/main/arduino-ide-board-package/libraries/Fri3dBadge2024/examples).

### Een schets uploaden met Arduino IDE
* Verbind de badge met je computer met een USB-C kabel.
* Selecteer de juiste USB-poort onder **Hulpmiddelen>Poort** (op een Mac is dit iets zoals `/dev/cu.usbserial-FFFFFFFF`).
    * Probleemoplossingstip: als je je board niet kunt zien, zorg er dan voor dat het is ingeschakeld en is aangesloten met een goede USB-kabel.
* Compileer en upload de code met **Schets>Uploaden**.
    * Probleemoplossingstip: Als het uploaden mislukt terwijl het compileren wel succesvol was, moet je de badge mogelijk handmatig in de bootmodus zetten. Houd daarvoor de boot-knop ingedrukt en druk vervolgens op de reset-knop. Na een seconde kun je de boot-knop loslaten.
* Pas de voorbeelden aan en experimenteer!

#### Installeren van bibliotheekafhankelijkheden voor Arduino Sketches
Om met randapparaten zoals het display op de badge te werken, moet je enkele bibliotheken installeren. De vereiste bibliotheken voor een voorbeeld staan altijd bovenaan de schets vermeld.

### Het starten van de voorbeeld schets in de main firmware
* Selecteer "Micropython" in het main firmware launcher menu op de badge.
    * Als je de main firmware nog niet hebt geïnstalleerd, bekijk dan eerst [onze reset-gids](../reset.nl.md).
* Je schets zal nu starten.
    * Let op: Het resetten van de esp brengt je terug naar de main firmware.

### Alternatieve uploadoptie: de fri3d badge main firmware niet gebruiken
#### Uitleg over normaal schets uploaden
Als je ons fri3d-esp32 boards manager pakket gebruikt, wordt esp_tool zo geconfigureerd dat het alleen naar de micropython-partitie (op adres 0x410000) schrijft. De main firmware moet dan de esp32 aanwijzen om vanaf die partitie te starten. Dit gebeurt wanneer je `Micropython` selecteert in het hoofdmenu op de badge.

#### Wat te doen als je de fri3d badge main firmware niet wilt gebruiken
Als je in plaats daarvan de main firmware wilt overschrijven, volg dan deze stappen:

* Selecteer de **EspTool** optie via **Hulpmiddelen>Programmer** in de Arduino IDE.
* Selecteer **Schets>Uploaden met Programmer** in het Arduino IDE-menu.
    * Let op: Als je dit hebt gedaan en terug wilt naar de main firmware, moet je [onze reset-gids](../reset.nl.md) volgen.
