# Hardware & Schaltplan

Für den Bau eines Prototypen werden die folgenden Komponenten benötigt.

## Komponentenliste

| Komponente | Spezifikation / Beispiel | Zweck |
| --- | --- | --- |
| **Mikrocontroller** | ESP32 Dev-Kit (z.B. Lolin D32, Adafruit Huzzah32) | **Wichtig:** Muss einen **Schaltregler** haben. |
| **LEDs** | WS2812B / "NeoPixel" LED-Ring oder -Streifen | 10-30 LEDs pro Lampe |
| **Echtzeituhr (RTC)** | DS3231 Modul | Zeitsteuerung & Aufwecken aus dem Deep Sleep |
| **Lichtsensor** | BH1750 oder TSL2561 Modul | Messung der Umgebungshelligkeit |
| **Akku** | LiPo-Akku, 3.7V | Kapazität je nach Größe (z.B. 2500mAh) |
| **Lademodul** | TP4056-basiertes Modul | Laden des LiPo-Akkus |
| **Ladekontakte** | Pogo-Pins (2x pro Ladeplatz) & Kupferflächen (2x pro Lampe) | Robuste Verbindung zur Ladestation |
| **Spannungsteiler** | 2x Widerstände (z.B. 100kΩ) | Messung der Akkuspannung |

## Schaltplan / Verkabelung

Die Komponenten werden wie folgt mit dem ESP32 verbunden. Die Pin-Bezeichnungen können je nach ESP32-Board variieren.

| ESP32 Pin | Verbinden mit... | Anmerkung |
| --- | --- | --- |
| **3V3** | VCC von DS3231, BH1750 | Stromversorgung für Sensoren |
| **GND** | GND von allen Komponenten | Gemeinsame Masse |
| **GPIO 22 (SCL)** | SCL von DS3231 & BH1750 | I2C Clock-Leitung |
| **GPIO 21 (SDA)** | SDA von DS3231 & BH1750 | I2C Daten-Leitung |
| **GPIO 16** | Daten-Pin der WS2812B LEDs | Ansteuerung der LEDs |
| **GPIO 34 (ADC)** | Mitte des Spannungsteilers vom Akku | Messung der Akkuspannung |
| **GPIO 35** | SQW-Pin des DS3231 | Weck-Signal von der RTC |
| **5V (VIN)** | 5V-Ausgang des TP4056 Lademoduls | Stromversorgung des ESP32-Boards |
| **GND** | GND-Ausgang des TP4056 | Masse für Lademodul |

**Akku-Verkabelung:**
- Der LiPo-Akku wird an die `B+` und `B-` Anschlüsse des TP4056 gelötet.
- Die Pogo-Pin-Kontakte werden mit den `IN+` und `IN-` Anschlüssen des TP4056 verbunden.
