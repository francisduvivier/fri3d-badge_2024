# Flashing

![Reset to Firmware Neuralizer](neuralizer.jpg)

Als je programmeer-avonturen bizarre resultaten hebben opgeleverd, kan het zijn dat je wil teruggaan naar de originele software...

## Fri3d Camp Reset Booth

Tijdens Fri3d Camp, bij de "Badge EHBO" helpen we jou met plezier terug op weg!
Zoek naar de "badge reset firmware" booth op het kamp. We hebben alles voorzien :-)

## Web interface

De online flasher app werkt enkel met browsers gebaseerd op chrome(Chrome of Edge, niet Firefox of Safari).

1. download de meest recente `full_webflasher_*.zip` van <https://github.com/Fri3dCamp/badge_firmware/releases>
2. ga naar <https://fri3d-flasher.vercel.app/>
3. klik op het icoon om de zip file te uploaden die je zonet hebt gedownload
4. klik op de "begin te flashen" knop

Als het flashen mislukt omdat je badge elke zoveel seconden reset, kan je ze als volgt "forceren" om te luisteren naar een nieuwe upload:

1. Klik en houd de "start" knop in(Op ESP32 heet dit de "boot button")
2. Klik en laat de "reset" knop los
3. Je badge staat nu in "download" mode tot je opnieuw reset duwt

Je badge start nu in de default Fri3d App.

## ESP-IDF

Dit is de ingewikkelde versie en is het enkel waard als de web flasher niet werkt.

1. Als je badge om de paar seconden spontaan reset, kan je ze als volgt "forceren" om te luisteren naar een nieuwe upload:
    11. Klik en houd de "start" knop in (Op ESP32 heet dit de "boot button")
    12. Klik en laat de "reset" knop los
    13. Je badge staat nu in "download" mode tot je opnieuw reset duwt
2. installeer ESP-IDF <https://docs.espressif.com/projects/esp-idf/en/stable/esp32/get-started/index.html#installation>
3. Download de meest recente firmware op <https://github.com/Fri3dCamp/badge_2024_micropython>
4. in de command line interface, type:

        python -m esptool -p (PORT) -b 460800 --before default_reset --after no_reset --chip esp32s3 write_flash --flash_mode dio --flash_size 16MB --flash_freq 80m 0x0 bootloader.bin 0x8000 partition-table.bin 0x1d000 ota_data_initial.bin 0x30000 micropython.bin

