# Bedienungsanleitung

Diese Anleitung beschreibt die tägliche Nutzung der Lampe.

## Aufladen

- Um die Lampe zu laden, stelle sie einfach auf einen freien Platz in der Ladestation.
- Die Lade-LED an der Station zeigt den Status an (z.B. Rot für "lädt", Grün für "voll").
- Der USB-C-Anschluss an der Lampe selbst kann ebenfalls zum Laden verwendet werden, sollte aber nur als Notlösung dienen.

## Ein- und Ausschalten

- Die Lampe schaltet sich zu den im WLED-Interface konfigurierten Zeiten automatisch ein und aus.
- Standardmäßig ist sie so eingestellt, dass sie sich bei Einbruch der Dämmerung einschaltet und am späten Abend wieder ausschaltet.
- Ein manueller Taster zum Ein- und Ausschalten kann optional nachgerüstet werden.

## Betriebsmodi

Die Lampe hat zwei Hauptmodi:

1.  **Autonomer Modus (Standard):**
    - Die Lampe leuchtet in einem voreingestellten Effekt (z.B. Feuersimulation).
    - Die Helligkeit passt sich automatisch der Umgebung an.
    - In diesem Modus ist die Akkulaufzeit maximal.

2.  **Event-Modus (WLAN):**
    - Wenn die Lampe mit dem Event-WLAN verbunden ist, kann sie zentral von einem Lichttechniker gesteuert werden.
    - Sie wird zu einem Teil der gesamten Raumbeleuchtung und kann Farben und Effekte synchron mit anderen Lichtern ändern.
    - Der Stromverbrauch ist in diesem Modus höher.

## Konfiguration

Die Erstkonfiguration und die Anpassung von Effekten und Timern erfolgt über die WLED-Weboberfläche.

1.  Nach dem ersten Start spannt die Lampe ein eigenes WLAN mit dem Namen `WLED-AP` auf.
2.  Verbinde dich mit diesem WLAN (Passwort: `wled1234`).
3.  Öffne einen Browser und gehe zur Adresse `4.3.2.1`.
4.  Hier kannst du unter "Config" > "WiFi Setup" die Lampe mit deinem normalen WLAN verbinden.
5.  Danach ist die Lampe unter ihrer neuen IP-Adresse in deinem Netzwerk erreichbar.
