# To-Do: PCB (Leiterplattenentwicklung)

Dies ist der Fahrplan zur Erstellung einer maßgeschneiderten Platine für die Lampe.

- [ ] **1. Prototyping auf dem Breadboard**
    - [ ] Alle in `docs/hardware.md` definierten Verbindungen auf einem Steckbrett (Breadboard) aufbauen.
    - [ ] Sicherstellen, dass die Schaltung mit der Firmware wie erwartet funktioniert. Dies ist der funktionale Beweis, bevor Arbeit in das PCB-Design fließt.

- [ ] **2. Schaltplan-Erstellung (Schematic)**
    - [ ] Eine PCB-Design-Software auswählen (Empfehlung: **KiCad**, da Open Source und sehr leistungsfähig).
    - [ ] Die funktionierende Breadboard-Schaltung in einen sauberen, digitalen Schaltplan in KiCad übertragen.
    - [ ] Alle Bauteile und Verbindungen korrekt definieren.

- [ ] **3. PCB-Layout**
    - [ ] Die physische Form und Größe der Platine definieren, damit sie perfekt in das 3D-gedruckte Gehäuse passt.
    - [ ] Die Bauteile auf der Platine platzieren. Position von Anschlüssen (USB-C), LEDs und Ladekontakten muss mit dem Gehäuse-Design übereinstimmen.
    - [ ] Die elektrischen Verbindungen (Leiterbahnen/Tracks) zwischen den Bauteilen ziehen.
    - [ ] Masseflächen (Copper Pours) für eine stabile Stromversorgung und zur Reduzierung von Störungen anlegen.

- [ ] **4. Verifizierung & Fertigungsdaten**
    - [ ] **Design Rule Check (DRC)** ausführen, um sicherzustellen, dass das Layout den Regeln des gewählten Herstellers (z.B. JLCPCB, PCBWay) entspricht.
    - [ ] Den Schaltplan nochmals mit dem Layout vergleichen (LVS - Layout vs. Schematic).
    - [ ] Die Gerber- und Bohr-Dateien exportieren. Dies sind die Standard-Dateien, die der Hersteller benötigt.
    - [ ] Eine Pick-and-Place-Datei und eine BOM (Bill of Materials) für die optionale maschinelle Bestückung (PCBA) erstellen.

- [ ] **5. Herstellung & Test**
    - [ ] Die Gerber-Dateien bei einem Hersteller hochladen und die Platinen bestellen.
    - [ ] Nach Erhalt die Bauteile auf die Platine löten (oder löten lassen).
    - [ ] Die fertige Platine ("Bring-up") testen: Zuerst nur mit Strom versorgen und auf Kurzschlüsse prüfen, dann den ESP32 flashen und die Funktionalität aller Komponenten (Sensoren, LEDs etc.) schrittweise validieren.
