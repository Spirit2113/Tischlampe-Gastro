# Projekt: Tischlampe für die Gastronomie

Dieses Dokument beschreibt die Anforderungen und den geplanten Technologie-Stack für die Entwicklung einer smarten Tischlampe für den Gastronomiebereich.

## Zusammenfassung

Ziel ist die Entwicklung einer akkubetriebenen, per USB-C ladbaren Tischlampe. Sie soll nicht nur als primäre Lichtquelle dienen, sondern auch Ambiente durch Spezialeffekte (z.B. eine Feuersimulation) schaffen können. Eine intelligente Steuerung über einen Timer und einen Umgebungslichtsensor soll den Betrieb automatisieren und optimieren.

## Kernfunktionen

- **Hauptbeleuchtung:** Angenehme, dimmbare Ausleuchtung des Tisches.
- **Spezialeffekte:** Implementierung von dynamischen Lichteffekten wie z.B. einer realistischen Feuersimulation.
- **Stromversorgung:** Integrierter Akku mit Ladefunktion über einen modernen USB-C-Anschluss.
- **Zeitsteuerung:** Ein programmierbarer Timer, der die Lampe zu festgelegten Zeiten automatisch ein- und ausschaltet.
- **Umgebungslichtsensor:** Automatische Anpassung der Helligkeit an das Umgebungslicht innerhalb des per Timer aktivierten Zeitraums.

## Potenzieller Technologie-Stack

- **Hardware-Plattform:** Ein Mikrocontroller wie der **ESP32** bietet sich an. Er ist kostengünstig, leistungsstark, verfügt über WLAN/Bluetooth (für eventuelle zukünftige Erweiterungen) und wird von einer großen Community unterstützt.
- **Firmware:** **C++** mit dem **Arduino Framework** oder **MicroPython** für eine schnelle und unkomplizierte Entwicklung.
- **Lichtquelle:** **Adressierbare LEDs (z.B. WS2812B "NeoPixel")** sind ideal, um komplexe Effekte wie die Feuersimulation darzustellen.
- **Sensorik:**
    - **Umgebungslicht:** Ein **BH1750** oder **TSL2561** Sensor für eine präzise Messung der Umgebungshelligkeit.
    - **Zeit:** Eine **Real-Time Clock (RTC)** wie die **DS3231** könnte für die Zeitsteuerung genutzt werden, um die Zeit auch bei Stromausfall zu halten.
- **Energie:** Eine **LiPo-Akkuzelle** in Kombination mit einem Lade- und Schutzmodul (**TP4056** mit USB-C-Anschluss).

## Nächste Schritte

1.  Erstellung eines privaten GitHub-Repositories für das Projekt.
2.  Auswahl und Beschaffung der initialen Hardware-Komponenten.
3.  Einrichtung der Entwicklungsumgebung (PlatformIO mit VS Code wird empfohlen).
4.  Beginn der Firmware-Entwicklung mit einem einfachen "Blink"-Sketch zur Validierung des Setups.
