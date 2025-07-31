# Projekt: Tischlampe für die Gastronomie

Dieses Dokument beschreibt die Anforderungen und den geplanten Technologie-Stack für die Entwicklung einer smarten, akkubetriebenen Tischlampe für den Gastronomiebereich mit dem Ziel einer Laufzeit von mindestens 12 Stunden.

## Zusammenfassung

Ziel ist die Entwicklung einer professionellen, robusten und effizienten Tischlampe. Sie kombiniert einen autonomen, energiesparenden Betriebsmodus für den Alltag mit einer zentralen Steuerungsmöglichkeit via **Art-Net** für Events. Ein durchdachtes Ladekonzept und eine mehrstufige Energiestrategie sind Kern des Entwurfs.

## Kernfunktionen

- **Hauptbeleuchtung:** Angenehme, dimmbare Ausleuchtung des Tisches (10-30 LEDs).
- **Spezialeffekte:** Dynamische Lichteffekte (Feuer, Farbverläufe etc.).
- **Zentrale Steuerung (Event-Modus):** Ansteuerung als **Art-Net-Knoten** über WLAN.
- **Autonomer Betrieb (Alltags-Modus):** Zeit- und helligkeitsgesteuerter Betrieb.
- **Professionelles Ladekonzept:** Zentrale **Ladestation mit Pogo-Pin-Kontakten**, um den USB-C-Port zu schonen.
- **Umfassendes Energiemanagement:**
    - Mehrstufige Schlafstrategie für maximale Akkulaufzeit.
    - Überwachung des Akkustands mit Benachrichtigungsfunktion via MQTT.

## Architektur & Technologie-Stack

Als Basis dient die **WLED**-Firmware auf einem **ESP32**, erweitert um spezifische **Usermods**.

### Hardware

- **Controller:** **ESP32**-Board mit hocheffizientem **Schaltregler (Buck/Step-Down)** und ohne unnötige "Power-On"-LED.
- **Firmware-Basis:** **WLED (https://kno.wled.ge/)**.
- **Lichtquelle:** 10-30 **Adressierbare LEDs** (WS2812B "NeoPixel").
- **Sensorik & Zeit:**
    - **Umgebungslicht:** **BH1750** oder **TSL2561** Sensor.
    - **Zeit & Weckfunktion:** Externe **Real-Time Clock (RTC) DS3231** für präzises Timing und das Aufwecken aus dem Deep Sleep.
- **Ladeelektronik:**
    - **Lampe:** Kontaktflächen für **Pogo-Pins** an der Unterseite, verbunden mit einem TP4056-basierten Lademodul. Der USB-C Port dient als Backup/Service-Schnittstelle.
    - **Ladestation:** Ein Gehäuse (Regal/Koffer) mit mehreren Ladeplätzen, die mit federgelagerten Pogo-Pins ausgestattet sind.

### Software & Energiestrategie

- **WLED-Konfiguration:**
    - **Automatic Brightness Limiter:** Feste Obergrenze für den maximalen Stromverbrauch der LEDs zum Schutz des Akkus und zur Gewährleistung einer Basislaufzeit.
    - **Sensor-Integration:** Die Helligkeit wird dynamisch an die Umgebung angepasst. Weniger Licht = weniger Verbrauch.
- **Mehrstufige Schlaf-Strategie (Usermod-Implementierung):**
    1.  **Modus "AUS" (z.B. tagsüber):**
        - **Zustand:** **Deep Sleep**. CPU, WLAN und LEDs sind komplett abgeschaltet.
        - **Verbrauch:** Minimal (wenige µA).
        - **Aufwachen:** Exklusiv durch ein Alarmsignal der externen RTC zur vordefinierten Zeit.
    2.  **Modus "AN & Verbunden" (Event-Betrieb):**
        - **Zustand:** **Modem Sleep**. Der ESP32 ist voll erreichbar (Art-Net, Web-UI), das WLAN-Modul schläft aber intelligent zwischen den Datenpaketen.
        - **Verbrauch:** Stark reduziert im Vergleich zu permanent aktivem WLAN.
    3.  **Modus "AN & Autonom" (Optionaler Max-Laufzeit-Modus):**
        - **Zustand:** WLAN wird per Usermod gezielt deaktiviert. Die Lampe läuft nur mit internem Timer und Sensor.
        - **Verbrauch:** Nochmals deutlich geringer, aber nicht mehr fernsteuerbar.
- **Akkustand & Benachrichtigung:** Ein Usermod liest die Akkuspannung und publiziert den Prozentwert via **MQTT**.

## Nächste Schritte

1.  **Prototypen-Hardware beschaffen:** ESP32-Board (auf Effizienz achten!), DS3231, BH1750, LEDs, Pogo-Pins, LiPo-Akku, Lademodul.
2.  **WLED-Entwicklungsumgebung aufsetzen:** PlatformIO mit VS Code. WLED-Sourcen klonen.
3.  **Proof of Concept (PoC) entwickeln:**
    - Standard-WLED flashen und Power-Limiter testen.
    - Usermods für Batterie, RTC (mit Deep Sleep) und Lichtsensor schrittweise integrieren und validieren.
    - Ersten Prototypen der Ladekontakte aufbauen und testen.
