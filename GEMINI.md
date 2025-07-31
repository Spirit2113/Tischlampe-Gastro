# Projekt: Tischlampe für die Gastronomie

Dieses Dokument beschreibt die Anforderungen und den geplanten Technologie-Stack für die Entwicklung einer smarten Tischlampe für den Gastronomiebereich.

## Zusammenfassung

Ziel ist die Entwicklung einer akkubetriebenen, per USB-C ladbaren Tischlampe. Sie soll nicht nur als primäre Lichtquelle dienen, sondern auch Ambiente durch Spezialeffekte (z.B. eine Feuersimulation) schaffen können. Eine intelligente Steuerung über einen Timer und einen Umgebungslichtsensor soll den Betrieb automatisieren und optimieren. Für den Einsatz bei Events soll die Lampe zentral per **Art-Net** steuerbar sein.

## Kernfunktionen

- **Hauptbeleuchtung:** Angenehme, dimmbare Ausleuchtung des Tisches.
- **Spezialeffekte:** Implementierung von dynamischen Lichteffekten (Feuer, Farbverläufe etc.).
- **Zentrale Steuerung (Events):** Ansteuerungsmöglichkeit als **Art-Net-Knoten** über WLAN zur Integration in professionelle Licht-Setups.
- **Autonomer Betrieb:** Zeit- und helligkeitsgesteuerter Modus für den normalen Gastronomie-Alltag.
- **Energiemanagement:**
    - Integrierter LiPo-Akku mit USB-C Ladefunktion.
    - **Deep-Sleep-Modus** für maximale Akkulaufzeit.
    - **Überwachung des Akkustands** mit Benachrichtigungsfunktion.

## Technologie-Stack & Architektur

Als Basis für die Firmware wird das Open-Source-Projekt **WLED** verwendet. Es bietet bereits eine riesige Fülle an Effekten, eine Weboberfläche zur Konfiguration und die benötigte Art-Net-Funktionalität. Die spezifischen Anforderungen dieses Projekts werden durch **benutzerdefinierte Erweiterungen (Usermods)** für WLED realisiert.

- **Hardware-Plattform:** **ESP32**. Bietet die nötige Leistung, WLAN und Low-Power-Modi.
- **Firmware-Basis:** **WLED (https://kno.wled.ge/)**.
- **Lichtquelle:** **Adressierbare LEDs** (z.B. WS2812B "NeoPixel").
- **Sensorik & Zeit:**
    - **Umgebungslicht:** **BH1750** oder **TSL2561** Sensor, angebunden über einen Usermod.
    - **Zeit & Deep Sleep:** Eine externe **Real-Time Clock (RTC) DS3231**. Sie ist essenziell, um den ESP32 aus dem Deep Sleep zeitgesteuert aufzuwecken und die Uhrzeit offline zu halten.
- **Energiemanagement:**
    - **Akku:** LiPo-Akkuzelle mit Schutzschaltung.
    - **Ladung:** Standard-Lademodul mit USB-C-Anschluss (z.B. auf Basis des TP4056).
    - **Akkustand-Überwachung:** Ein WLED-Usermod liest die Akkuspannung über einen Spannungsteiler an einem ADC-Pin des ESP32.
    - **Benachrichtigungen:** Der Akkustand wird per **MQTT** publiziert. Ein übergeordnetes System (z.B. Home Assistant) kann darauf basierend Push-Benachrichtigungen an ein Smartphone senden. Eine "intelligente Ladestation" mit eigenem Mikrocontroller könnte den Status ebenfalls abfragen und visualisieren.

## Nächste Schritte

1.  **Prototypen-Hardware beschaffen:** ESP32 Dev-Kit, DS3231 RTC, BH1750 Lichtsensor, WS2812B LED-Ring, LiPo-Akku und Lademodul.
2.  **WLED-Entwicklungsumgebung aufsetzen:** PlatformIO mit VS Code. WLED-Sourcen klonen.
3.  **Proof of Concept (PoC) entwickeln:**
    - Standard-WLED auf dem ESP32 zum Laufen bringen.
    - Einen vorhandenen "Battery"-Usermod integrieren und testen.
    - Einen Usermod für die Ansteuerung der DS3231 RTC und die Implementierung des Deep-Sleep-Zyklus entwickeln.
    - Den Lichtsensor-Usermod integrieren.
