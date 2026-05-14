# Low-Budget-Version – eine Kartonbox nur für die Maine Coon

Ziel: So billig wie möglich testen, ob RFID/NFC-Halsbandtag + automatische Tür für eine Katze funktioniert.

Diese Version ersetzt nicht die finale Holzbox. Sie ist ein Lern- und Funktionstest.

---

# Scope

Nur eine Box:

```text
1x Karton-/Foamboard-Box für die Maine Coon
1x Halsband mit NFC/RFID-Tag
1x Eingang mit leichter Tür
1x einfache Steuerung
```

Nicht enthalten:

```text
- zweite Box
- Futterpodest
- schöne Holzoptik
- Getriebemotor
- komplette Möbelkonstruktion
- App/Webinterface
```

---

# Zielbudget

```text
Minimal ohne Sicherheitssensor: ca. 25–45 €
Empfohlen mit Sicherheitssensor: ca. 35–60 €
Mit Kleinteile-Puffer: ca. 45–70 €
```

Wenn schon USB-Netzteil, Karton, Kabel oder Servo vorhanden sind, kann es günstiger werden.

---

# Minimalteile

| Teil | Menge | Zweck | Grobpreis |
|---|---:|---|---:|
| ESP32 Dev Board | 1 | Steuerung | 6–12 € |
| PN532 NFC/RFID Modul | 1 | Halsbandtag lesen | 7–15 € |
| NFC-Schlüsselanhänger / Tag 13,56 MHz | 1–2 | Chip am Halsband | 2–8 € |
| MG90S Servo oder SG90 Servo | 1 | leichte Tür bewegen | 3–10 € |
| USB-Netzteil 5V | 1 | Strom | 0–10 € |
| Karton / Foamboard | nach Bedarf | Gehäuse / Tür | 0–10 € |
| Tape / Heißkleber | nach Bedarf | Verstärkung | 0–10 € |

---

# Empfohlene Zusatzteile

| Teil | Menge | Zweck | Grobpreis |
|---|---:|---|---:|
| IR-Lichtschranke oder VL53L0X | 1 | Tür schließt nicht bei Blockade | 3–8 € |
| Notfall-Taster | 1 | manuell öffnen | 1–3 € |
| Status-LED | 1 | Debug/Status | 0–2 € |
| Jumper-Kabel | 1 Set | Verkabelung | 3–6 € |

---

# Billigste sinnvolle Version

Empfohlen wird nicht die absolute Minimalversion, sondern diese:

```text
ESP32
PN532
NFC-Halsbandtag
MG90S Servo
1x IR-Lichtschranke oder VL53L0X
Notfall-Taster
Karton/Foamboard
Tape/Heißkleber
```

Warum:

```text
Der Sensor verhindert, dass die Tür schließt, während Kopf/Pfote im Eingang ist.
```

---

# Türprinzip

Für die Low-Budget-Version:

```text
leichte seitliche Schiebetür
Servo zieht/schiebt über kurzen Hebel
Tür läuft in Karton-/Foamboard-Kanal
Mechanik ist verdeckt
```

Nicht verwenden:

```text
schwere Holztür
fallende Klappe
starke Feder
offene Schnur im Katzenraum
```

---

# Verdeckter Mechanikkanal

Auch bei Karton:

```text
Außenlage mit Eingang
Zwischenlage = Türkanal + Servo/Mechanik
Innenlage = glatte Schutzblende
```

Von innen darf die Katze nicht erreichen:

```text
Servo
Kabel
Schnur
Hebel
Sensorplatine
Elektronik
```

---

# Halsband / Tag

Für den Test reicht:

```text
Sicherheits-Katzenhalsband
+ kleiner NFC-Schlüsselanhänger oder flacher NFC-Tag
```

Wichtig:

```text
Nur Sicherheitsverschluss verwenden.
Tag so klein/leicht wie möglich.
Tag muss nah genug am PN532 vorbeikommen.
```

---

# Erste Maße für Karton-Prototyp

Für Maine Coon nicht zu eng:

```text
Eingang: ca. 30 x 35 cm
Box grob: 60–80 cm breit, 50–60 cm tief, 50–60 cm hoch
```

Für den ersten reinen Türtest reicht auch nur eine Frontplatte:

```text
Kartonfront mit Eingang
Servo-Türmodul
kein kompletter Innenraum nötig
```

---

# Teststufen

## Stufe 1: RFID-Tischtest

```text
ESP32 + PN532
Tag-ID auslesen
richtigen Tag speichern
```

## Stufe 2: Servo-Test

```text
richtiger Tag → Servo öffnet
falscher Tag → bleibt geschlossen
```

## Stufe 3: Türtest ohne Katze

```text
leichte Kartontür öffnet/schließt
Mechanik verdeckt
Tür klemmt nicht
```

## Stufe 4: Sensor-Test

```text
Hand im Eingang → Tür schließt nicht
Hand während Schließen → Servo stoppt/öffnet wieder
```

## Stufe 5: Katzentraining

```text
Tür zuerst offen lassen
Leckerli/Futter rein
RFID nur loggen
später Öffnen aktivieren
Schließen erst ganz am Ende aktivieren
```

---

# Realistische Erwartung

Diese Version testet:

```text
- RFID-Position
- Halsbandtag-Erkennung
- Reaktion der Katze auf Eingang/Tür
- Grundlogik im Code
- ob die Idee überhaupt alltagstauglich wirkt
```

Sie testet noch nicht zuverlässig:

```text
- langlebige Mechanik
- perfekte Geräuscharmut
- schöne Reinigung
- finale Holzbauform
```

---

# Wichtigste Sicherheitsregel

```text
Wenn es unsicher wirkt, Tür offen lassen.
```

Futterklau ist weniger schlimm als eine eingeklemmte oder gestresste Katze.
