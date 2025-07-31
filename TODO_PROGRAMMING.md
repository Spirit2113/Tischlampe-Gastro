# To-Do: Programmierung (Firmware)

Dies ist der Fahrplan für die Entwicklung der WLED-basierten Firmware.

- [ ] **1. Entwicklungsumgebung einrichten**
    - [ ] VS Code installieren.
    - [ ] PlatformIO IDE Extension in VS Code installieren.
    - [ ] WLED-Repository von GitHub klonen.
    - [ ] Projekt in PlatformIO öffnen und sicherstellen, dass es kompiliert.

- [ ] **2. Basis-Funktionstest (Proof of Concept)**
    - [ ] Standard-WLED auf dem ESP32-Prototypen flashen.
    - [ ] Mit dem `WLED-AP` verbinden und WLAN-Zugangsdaten konfigurieren.
    - [ ] Erreichbarkeit der Weboberfläche im eigenen WLAN testen.
    - [ ] Grundlegende LED-Effekte und Farben steuern, um die korrekte Verkabelung zu prüfen.

- [ ] **3. Usermod-Integration & Entwicklung**
    - [ ] **Akku-Überwachung:** Einen vorhandenen "Battery"-Usermod finden, integrieren und die korrekte Spannungsanzeige in der UI validieren.
    - [ ] **Lichtsensor-Integration:** Einen Usermod für den BH1750-Sensor integrieren. Die Lux-Werte über die serielle Konsole oder in der UI ausgeben.
    - [ ] **RTC-Integration:** Einen Usermod für die DS3231-RTC integrieren. Sicherstellen, dass die korrekte Uhrzeit gelesen und gehalten wird.
    - [ ] **Logik für Auto-Helligkeit:** Code schreiben, der den Wert des Lichtsensors nutzt, um die globale Helligkeit in WLED anzupassen.
    - [ ] **Logik für Deep Sleep:** Den RTC-Usermod erweitern, um den ESP32 in den Deep Sleep zu versetzen und per RTC-Alarm wieder aufzuwecken.

- [ ] **4. Energieoptimierung & Tests**
    - [ ] Stromverbrauch im Deep-Sleep-Modus messen und validieren (< 1mA).
    - [ ] Stromverbrauch im "Modem Sleep" (normaler WLAN-Betrieb) messen.
    - [ ] Den "Automatic Brightness Limiter" in WLED konfigurieren und testen.
    - [ ] Einen 12-Stunden-Dauertest mit einem voll geladenen Akku durchführen, um die Laufzeit in der Praxis zu validieren.

- [ ] **5. Code-Finalisierung**
    - [ ] Code aufräumen und unnötige Debug-Ausgaben entfernen.
    - [ ] Kommentare für komplexe Logik-Teile hinzufügen.
    - [ ] Eine stabile Release-Version (`.bin`-Datei) erstellen, die einfach von anderen Nutzern geflasht werden kann.
