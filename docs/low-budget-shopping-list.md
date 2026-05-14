# Low-Budget Shopping List – Maine-Coon Kartonbox mit Sensor

Ziel: Eine möglichst günstige erste Testversion nur für die Maine Coon bauen.

Diese Version verwendet vorhandene Näpfe und eine vorhandene Silikonmatte. Es werden keine neuen Näpfe, kein Futterpodest und kein herausnehmbarer Einsatz gekauft.

---

# Scope

```text
1 Box
1 Katze / Maine Coon
Karton oder Foamboard
RFID/NFC-Halsbandtag
leichte Servo-Schiebetür
1 Sicherheitssensor gegen Einklemmen
vorhandene Näpfe
vorhandene Silikonmatte
```

---

# Nicht kaufen für diese Version

```text
Keine Kerbl-Näpfe
Kein Futterpodest
Keine Einsatzplatte
Keine Holzbox
Kein Getriebemotor
Kein Motortreiber
Keine Schnurschleife
Keine Umlenkrollen
Keine großen U-Schienen
```

---

# Pflichtteile

| Teil | Menge | Amazon-Suchbegriff | Grobpreis |
|---|---:|---|---:|
| ESP32 Dev Board | 1 | `ESP32 DevKit USB-C` | 6–12 € |
| PN532 NFC/RFID Modul | 1 | `PN532 NFC RFID Modul I2C SPI UART` | 7–15 € |
| NFC-Tag / Schlüsselanhänger 13,56 MHz | 1–2 | `NFC Schlüsselanhänger NTAG213` | 2–8 € |
| Sicherheits-Katzenhalsband | 1 | `Katzenhalsband Sicherheitsverschluss` | 3–8 € |
| MG90S Servo | 1 | `MG90S Servo Metallgetriebe` | 4–10 € |
| IR-Lichtschranke | 1 | `IR Lichtschranke Modul Arduino` | 3–8 € |
| Notfall-Taster | 1 | `Drucktaster Arduino momentary` | 1–3 € |
| Jumper-Kabel Set | 1 | `Dupont Kabel Set Arduino` | 3–6 € |
| USB-Netzteil 5V | 1 | `USB Netzteil 5V 2A` | 0–8 € |
| Karton / Foamboard | nach Bedarf | `Foamboard 5mm` optional | 0–10 € |
| Gewebeband / Panzertape | nach Bedarf | `Gewebeband stark` | 0–8 € |
| Heißkleber / Kleber | nach Bedarf | `Heißklebesticks` | 0–8 € |

---

# Realistisches Budget

Wenn nichts vorhanden ist:

```text
ca. 35–70 €
```

Wenn USB-Netzteil, Karton, Kabel, Tape oder Kleber vorhanden sind:

```text
ca. 25–50 €
```

---

# Empfohlenes Minimal-Setup

```text
ESP32
PN532
NFC-Tag am Sicherheits-Halsband
MG90S Servo
IR-Lichtschranke
Notfall-Taster
Karton/Foamboard
vorhandene Näpfe
vorhandene Silikonmatte
```

---

# Warum IR-Lichtschranke statt VL53L0X?

Für den billigsten Prototyp ist eine Lichtschranke einfacher:

```text
Lichtstrahl frei = Tür darf schließen
Lichtstrahl unterbrochen = Tür bleibt offen
```

Das ist weniger Kalibrierung als ein Abstandssensor.

---

# Prototyp-Aufbau

## Kartonbox

```text
Box groß genug für Maine Coon
Eingang ca. 30 x 35 cm
vorhandene Silikonmatte auf den Boden
vorhandene Näpfe auf die Matte
```

## Tür

```text
leichte seitliche Schiebetür aus Karton/Foamboard
mit Tape verstärkt
Servo bewegt Tür über kleinen Hebel oder Schubstange
```

## Mechanikschutz

Auch bei der Kartonversion Pflicht:

```text
Servo verdeckt
Kabel verdeckt
Türmechanik verdeckt
Katze darf nichts davon erreichen
```

Empfohlene Schichten:

```text
Außenfront mit Eingang
Zwischenraum = Türkanal + Servo
Innenblende = glatte Schutzwand
Katzenraum
```

---

# Minimal-Logik

```text
richtiger NFC-Tag erkannt
→ Servo öffnet Tür

Tür bleibt offen, solange Lichtschranke blockiert ist

wenn Lichtschranke frei ist
→ 2–3 Sekunden warten
→ Servo schließt Tür langsam

wenn Notfall-Taster gedrückt
→ Tür öffnet
```

---

# Testreihenfolge

```text
1. ESP32 startet.
2. PN532 liest NFC-Tag.
3. Tag-ID im seriellen Monitor ausgeben.
4. Servo einzeln öffnen/schließen lassen.
5. Lichtschranke frei/blockiert testen.
6. RFID + Servo kombinieren.
7. RFID + Servo + Lichtschranke kombinieren.
8. Karton-Tür ohne Katze testen.
9. Türmechanik verdecken.
10. Katze mit offener Tür an die Box gewöhnen.
11. Erst später automatisches Schließen aktivieren.
```

---

# Sicherheitsregeln

```text
Keine sichtbaren Kabel im Katzenraum.
Keine sichtbare Schnur im Katzenraum.
Keine offene Servo-Mechanik im Katzenraum.
Keine harte/schwere Tür.
Tür nur schließen, wenn Lichtschranke frei ist.
Bei Unsicherheit Tür offen lassen.
```

---

# Ergebnis

Diese Version soll nicht schön sein. Sie soll nur billig testen:

```text
- erkennt die Box den Halsbandchip?
- akzeptiert die Maine Coon den Eingang?
- funktioniert eine leichte Tür?
- reicht die Sensorlogik?
- lohnt sich danach der Holzbau?
```
