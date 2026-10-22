<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# Datenblatt: Waveshare ESP32-S3-Touch-LCD-7

Das Board ist ein ESP32-S3-Entwicklungsboard mit integriertem 7-Zoll-Kapazitiv-Touchdisplay und eignet sich sehr gut für eine Smart-Home-Oberfläche mit LVGL, MQTT/WebSocket-Kommunikation und lokalen Steuerungen.[^1][^2]

## Übersicht

| Eigenschaft | Wert |
| :-- | :-- |
| Modell | Waveshare ESP32-S3-Touch-LCD-7 [^1] |
| Anwendung | HMI / Smart-Home-Touchpanel, IoT-Steuerung [^2] |
| Prozessor | ESP32-S3, Xtensa 32-bit LX7 Dual-Core, bis 240 MHz [^1] |
| Funk | 2,4-GHz-WLAN 802.11 b/g/n, Bluetooth 5 LE, integrierte Antenne [^1] |
| Display | 7" IPS-LCD, 800 × 480 px, 65K Farben [^1] |
| Touch | Kapazitiv, 5-Punkt-Touch, I²C, Interrupt-Unterstützung [^2] |
| Betriebsspannung | 5 V [^1] |
| Stromaufnahme | ca. 450 mA bei 5 V [^1] |
| Temperaturbereich | 0 °C bis 65 °C [^1] |
| Abmessungen | 192,96 × 110,76 mm mit Touch [^1] |

## Prozessor und Speicher

| Komponente | Spezifikation |
| :-- | :-- |
| MCU | ESP32-S3, Dual-Core Xtensa LX7 [^1] |
| Taktfrequenz | bis 240 MHz [^1] |
| SRAM | 512 KB [^1] |
| ROM | 384 KB [^1] |
| Flash | 8 MB bzw. 16 MB, je nach Boardvariante [^3][^4] |
| PSRAM | 8 MB [^3][^4] |

Für eine Smart-Home-Oberfläche sind 8 MB PSRAM und 8–16 MB Flash ausreichend dimensioniert: LVGL-Widgets, mehrere Screens, Icons, Konfigurationsdaten und Netzwerk-Stacks lassen sich damit komfortabel umsetzen.[^2][^4]

## Display und Touch

| Merkmal | Wert |
| :-- | :-- |
| Displaygröße | 7 Zoll [^1] |
| Auflösung | 800 × 480 Pixel [^1] |
| Paneltyp | IPS [^1] |
| Farben | 65K [^1] |
| Sichtwinkel | 170° [^1] |
| Helligkeit | 345 cd/m² [^1] |
| Display-Interface | RGB [^5] |
| Display-Controller | ST7262 [^5] |
| Touch-Controller | GT911 [^5] |
| Touchpunkte | 5 [^2] |
| Touch-Interface | I²C mit Interrupt [^2] |

Die 800 × 480er-Auflösung eignet sich für typische Smart-Home-Layouts: Raumübersicht, Heizung/Licht/Jalousien, Szenen-Auswahl, Diagramme und Statusanzeigen gleichzeitig.[^1][^2]

## Schnittstellen

- USB-C für Stromversorgung, Programmierung und Kommunikation; zusätzlich USB-UART-Konverter.[^3]
- I²C-Schnittstelle, unter anderem für Touch, Sensoren und Erweiterungen.[^2][^3]
- RS-485-Schnittstelle, nützlich für industrielle Sensoren, Modbus-Geräte oder Gebäudeautomation.[^3][^2]
- CAN-Bus-Schnittstelle.[^2][^3]
- UART-Schnittstellen für externe Module.[^3]
- MicroSD-/TF-Kartenslot für Konfigurationen, Logs, Bilder oder UI-Assets.[^2][^3]
- Kamera-Interface, 3,5-mm-Kopfhörerausgang und Grove-Anschlüsse sind je nach Produktvariante vorhanden.[^4]
- PH2.0-Anschluss für einen 3,7-V-Lithium-Akku.[^3]


## Smart-Home-Eignung

| Anforderung | Eignung |
| :-- | :-- |
| Touchbedienung | Sehr gut: 5-Punkt-Kapazitivtouch mit GT911 [^5][^2] |
| Grafische Oberfläche | Sehr gut: LVGL wird vom Hersteller ausdrücklich genannt [^2] |
| WLAN-Integration | Sehr gut: 2,4-GHz-WLAN für MQTT, HTTP, WebSocket, Home Assistant etc. [^1] |
| Bluetooth | Gut für BLE-Sensoren, Beacons oder Konfiguration [^1] |
| Lokale Busanbindung | Sehr gut durch CAN, RS-485 und I²C [^2][^3] |
| Datenspeicherung | Gut durch MicroSD und großen Flash/PSRAM [^2][^3] |
| Dauerbetrieb | Geeignet, jedoch Belüftung und stabile 5-V-Versorgung beachten [^1] |

## Entwicklung

- Programmierung über ESP-IDF, Arduino IDE oder PlatformIO.[^2]
- Für die UI ist **LVGL** die empfohlene Grafikbibliothek; Waveshare nennt LVGL explizit als geeignete Lösung für dieses Board.[^2]
- Der CH422G-I/O-Expander steuert unter anderem Reset und Hintergrundbeleuchtung des Displays.[^6]
- Für Home Assistant bietet sich eine Architektur mit MQTT oder WebSocket an: Das Board stellt die lokale Touch-UI bereit, während Zustände, Automationen und Geräteintegration im Smart-Home-Server laufen.


## Hinweise für den Einsatz

- Das Display benötigt eine stabile 5-V-Stromversorgung; als Richtwert nennt Waveshare 450 mA, bei hoher Helligkeit und WLAN-Aktivität sollte die Versorgung Reserve haben.[^1]
- Die Touch-Version ist mit 192,96 × 110,76 mm deutlich größer als die Version ohne Touch; das ist für Gehäuse- und Wandmontage relevant.[^1]
- Für ein Wandpanel empfiehlt sich ein Gehäuse mit Zugang zu USB-C bzw. externer 5-V-Versorgung sowie gegebenenfalls RS-485/I²C nach außen.[^3]
- Der Betrieb ist für 0–65 °C spezifiziert; in Wanddosen oder hinter Glas sollte die Wärmeentwicklung berücksichtigt werden.[^1]

<span style="display:none">[^10][^11][^12][^13][^14][^15][^7][^8][^9]</span>

<div align="center">⁂</div>

[^1]: https://docs.waveshare.com/ESP32-S3-Touch-LCD-7

[^2]: https://www.waveshare.com/wiki/ESP32-S3-Touch-LCD-7

[^3]: https://kamami.pl/en/esp32/1195674-esp32-s3-7inch-capacitive-touch-display-development-board-esp32-with-display-800-480-5-point-touc-5902186314610.html

[^4]: https://www.berrybase.de/en/product-datasheet/019234a64c8e70fbb657d6ab5a641ce9/create

[^5]: https://www.waveshare.com/esp32-s3-lcd-7b.htm

[^6]: https://docs.waveshare.com/ESP32-S3-Touch-LCD-7/Instructions-For-Use

[^7]: https://nuttx.apache.org/docs/latest/platforms/xtensa/esp32s3/boards/esp32s3-touch-lcd7/index.html

[^8]: https://docs.waveshare.com/ESP32-S3-Touch-LCD-7C-BOX

[^9]: https://docs.waveshare.net/ESP32-S3-Touch-LCD-7/

[^10]: https://files.waveshare.com/wiki/ESP32-S3-Touch-LCD-7/ESP32-S3-Touch-LCD-7-Sch.pdf

[^11]: https://docs.waveshare.com/ESP32-S3-Touch-LCD-7/Resources-And-Documents

[^12]: https://www.amazon.com/ESP32-S3-7inch-Capacitive-Development-LCD/dp/B0D6XSY476

[^13]: https://www.digitec.ch/en/s1/product/waveshare-esp32-s3-7inch-capacitive-touch-display-development-board-800x480-single-board-computer-ki-46580286

[^14]: https://www.amazon.com/Waveshare-Capacitive-Development-Frequency-Bluetooth/dp/B0D2NMCY7K

[^15]: https://www.atomic14.com/esp32/boards/waveshare-esp32-s3-touch-lcd-7/
