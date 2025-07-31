# Firmware-Einrichtung

Die Firmware basiert auf dem Open-Source-Projekt **WLED**. Wir kompilieren eine eigene Version mit den benötigten Erweiterungen (Usermods).

## 1. Benötigte Software installieren

1.  **Visual Studio Code:** Lade und installiere den kostenlosen Code-Editor [VS Code](https://code.visualstudio.com/).
2.  **PlatformIO IDE:** Öffne VS Code, gehe zum Extensions-Tab (das Icon mit den vier Quadraten) und suche und installiere die **PlatformIO IDE** Erweiterung.

## 2. WLED-Quellcode herunterladen

1.  Öffne ein Terminal oder eine Kommandozeile.
2.  Klone das WLED-Repository auf deinen Computer mit folgendem Befehl:
    ```bash
    git clone https://github.com/Aircoookie/WLED.git
    ```
3.  Öffne den heruntergeladenen `WLED` Ordner in VS Code (`File > Open Folder...`).

## 3. Usermods konfigurieren

Die spezielle Funktionalität unserer Lampe wird durch Usermods realisiert.

1.  Navigiere im WLED-Projekt zum Ordner `wled00/`.
2.  Kopiere die Datei `usermods_list.cpp.example` und benenne die Kopie in `usermods_list.cpp` um.
3.  Öffne `usermods_list.cpp` und aktiviere die benötigten Usermods, indem du die `//` vor den entsprechenden `#include`-Zeilen entfernst. Für unser Projekt sind dies voraussichtlich:
    - Ein Usermod für die Batterie-Anzeige (`usermod_v2_battery.h`)
    - Ein Usermod für die RTC (`usermod_ds3231.h` - muss evtl. aus der Community bezogen werden)
    - Ein Usermod für den Lichtsensor (`usermod_bh1750.h` - muss evtl. aus der Community bezogen werden)

## 4. Kompilieren und Hochladen

1.  PlatformIO sollte automatisch den richtigen `esp32` Build-Typ erkennen.
2.  Passe die `platformio.ini` bei Bedarf an (z.B. Pin-Belegungen für die Usermods).
3.  Verbinde den ESP32 per USB mit deinem Computer.
4.  Klicke auf den kleinen Pfeil (`->`) in der blauen Statusleiste am unteren Rand von VS Code, um den Code zu kompilieren und auf den ESP32 hochzuladen.
