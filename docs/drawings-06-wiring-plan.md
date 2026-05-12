# Zeichnungspaket 06 – Verdrahtungsplan + ESP32-Pinplan + Stromverteilung

Dieses Dokument beschreibt die geplante Verkabelung pro Box: Stromversorgung, ESP32-Pinplan, RFID/NFC, Innensensor, Motortreiber, Endschalter, Lichtschranken, Notfall-Taster und Status-LED.

Status: Planungsstand / erste elektrische Blaupause. Exakte Pinbelegung kann später angepasst werden, wenn das konkrete ESP32-Board und die realen Module feststehen.

---

# Ziel dieses Zeichnungspakets

Die Verdrahtung soll:

- übersichtlich und wartbar sein
- pro Box unabhängig funktionieren
- 12V-Motor und 5V/3,3V-Logik sauber trennen
- Sensoren zuverlässig auslesen
- Motor sicher über Motortreiber steuern
- keine 5V-Signale direkt auf ESP32-GPIOs geben
- spätere Fehlersuche erleichtern

---

# Grundarchitektur pro Box

```text
12V Netzteil
   │
   ├── Sicherung empfohlen
   │
   ├── Hauptschalter
   │
   ├── 12V → TB6612FNG Motorversorgung → 12V Getriebemotor
   │
   └── 12V → Step-Down 5V → ESP32 / Sensorik / RFID
```

Wichtig:

```text
Alle GND-Leitungen müssen gemeinsam verbunden sein.
```

---

# Hauptkomponenten pro Box

```text
ESP32 Dev Board
PN532 RFID/NFC Modul
VL53L0X Innensensor
TB6612FNG Motortreiber
12V DC Getriebemotor
2x IR-Lichtschranke
2x Endschalter
1x Notfall-Taster
1x RGB-LED oder Status-LED
1x Step-Down 12V → 5V
1x 12V/2A Netzteil
1x Hauptschalter
1x Sicherung empfohlen
```

---

# Stromverteilung

## 12V-Seite

```text
+12V Netzteil
   │
   ├── Sicherung 2A empfohlen
   │
   ├── Hauptschalter
   │
   ├── VM / Motorversorgung am TB6612FNG
   │
   └── Eingang Step-Down 12V → 5V
```

## 5V-Seite

```text
Step-Down 5V Ausgang
   │
   ├── ESP32 VIN/5V Pin
   ├── PN532, falls 5V-tolerantes Modul
   ├── Lichtschranken, falls 5V-Version
   └── sonstige 5V-Module
```

## 3,3V-Seite

```text
ESP32 3V3 Pin
   │
   ├── PN532, falls mit 3,3V betrieben
   ├── VL53L0X
   └── Pullups / Logik nach Bedarf
```

Achtung:

```text
ESP32 GPIOs sind 3,3V-Logik.
Keine 5V-Ausgänge direkt auf GPIOs führen.
```

---

# Gemeinsame Masse

Alle Massen verbinden:

```text
GND Netzteil
GND Step-Down Eingang
GND Step-Down Ausgang
GND ESP32
GND PN532
GND VL53L0X
GND TB6612FNG
GND Motorversorgung
GND Lichtschranken
GND Endschalter/Taster
GND LED
```

Ohne gemeinsame Masse funktionieren die Steuersignale nicht zuverlässig.

---

# Vorläufiger ESP32-Pinplan

| Funktion | ESP32 Pin | Hinweis |
|---|---:|---|
| I2C SDA | GPIO 21 | PN532 + VL53L0X |
| I2C SCL | GPIO 22 | PN532 + VL53L0X |
| Motor AIN1 | GPIO 25 | TB6612FNG |
| Motor AIN2 | GPIO 26 | TB6612FNG |
| Motor PWM | GPIO 27 | TB6612FNG PWMA |
| Motor STBY | GPIO 14 | TB6612FNG Standby |
| Endschalter offen | GPIO 32 | Eingang mit Pullup |
| Endschalter geschlossen | GPIO 33 | Eingang mit Pullup |
| Lichtschranke unten | GPIO 34 | Input-only |
| Lichtschranke oben | GPIO 35 | Input-only |
| Notfall-Taster | GPIO 18 | Eingang mit Pullup |
| RGB Rot | GPIO 19 | optional |
| RGB Grün | GPIO 23 | optional |
| RGB Blau | GPIO 5 | optional |

Hinweis:

```text
GPIO 34 und GPIO 35 sind nur Eingänge.
Das ist perfekt für Sensor-Eingänge.
```

---

# I2C-Bus

Am I2C-Bus hängen:

```text
PN532 RFID/NFC Modul
VL53L0X Innensensor
```

Verdrahtung:

```text
ESP32 GPIO 21 SDA ─── SDA PN532
                   └── SDA VL53L0X

ESP32 GPIO 22 SCL ─── SCL PN532
                   └── SCL VL53L0X

GND gemeinsam
3,3V oder 5V je nach Modul
```

Wichtig:

```text
PN532 und VL53L0X brauchen unterschiedliche I2C-Adressen.
Normalerweise ist das der Fall.
```

Falls es Adress- oder Stabilitätsprobleme gibt:

```text
- PN532 auf SPI wechseln
oder
- separaten I2C-Bus verwenden
```

Für Version 1 bleibt I2C als Standard gesetzt.

---

# PN532 RFID/NFC Modul

## Zweck

```text
RFID/NFC-Halsbandtag lesen.
Nur erlaubter Tag öffnet die jeweilige Box.
```

## Anschluss über I2C

```text
PN532 VCC  → 3,3V oder 5V je nach Modul
PN532 GND  → GND
PN532 SDA  → ESP32 GPIO 21
PN532 SCL  → ESP32 GPIO 22
```

Achtung:

```text
Vor Anschluss prüfen, ob das konkrete PN532-Modul 3,3V-Logik unterstützt.
```

---

# VL53L0X Innensensor

## Zweck

```text
Erkennt Katze innen am Ausgang.
Wenn innen Katze erkannt wird, öffnet die Tür immer.
```

## Anschluss

```text
VL53L0X VIN/VCC → 3,3V oder 5V je nach Breakout
VL53L0X GND     → GND
VL53L0X SDA     → ESP32 GPIO 21
VL53L0X SCL     → ESP32 GPIO 22
```

Empfohlene Logik im Code:

```text
Abstand kleiner als Grenzwert → Katze will raus
```

Start-Grenzwert:

```text
Standardbox: ca. 300–350 mm
Largebox:    ca. 350–450 mm
```

Wird später praktisch kalibriert.

---

# TB6612FNG Motortreiber

## Zweck

Der ESP32 steuert den Motor nicht direkt, sondern über den TB6612FNG.

```text
ESP32 → TB6612FNG → 12V Getriebemotor
```

## Anschluss Steuersignale

```text
TB6612FNG AIN1 → ESP32 GPIO 25
TB6612FNG AIN2 → ESP32 GPIO 26
TB6612FNG PWMA → ESP32 GPIO 27
TB6612FNG STBY → ESP32 GPIO 14
```

## Anschluss Versorgung

```text
TB6612FNG VM   → +12V Motorversorgung
TB6612FNG VCC  → Logikspannung passend zum Modul, meist 3,3V/5V
TB6612FNG GND  → gemeinsame Masse
Motor A01/A02  → 12V Getriebemotor
```

## Motorlogik

```text
AIN1/AIN2 bestimmen Richtung.
PWMA bestimmt Geschwindigkeit per PWM.
STBY aktiviert/deaktiviert den Treiber.
```

---

# Getriebemotor

## Anschluss

```text
Motorleitung 1 → TB6612FNG A01
Motorleitung 2 → TB6612FNG A02
```

Wenn Öffnen/Schließen vertauscht ist:

```text
Motorleitungen tauschen
oder
Richtung im Code invertieren
```

Empfohlen:

```text
Motorkabel verdrillen.
Motorkabel nicht direkt parallel an RFID-Leitung führen.
```

---

# Endschalter

## Zweck

```text
Endschalter offen: Tür ist komplett offen.
Endschalter geschlossen: Tür ist komplett geschlossen.
```

## Anschluss mit internem Pullup

```text
ESP32 Pin → Endschalter → GND
```

Logik:

```text
nicht gedrückt = HIGH
gedrückt     = LOW
```

## Pins

```text
Endschalter offen      → GPIO 32
Endschalter geschlossen → GPIO 33
```

Vorteil:

```text
Keine externe 5V-Spannung nötig.
Sicher für ESP32.
```

---

# Notfall-Taster

## Zweck

```text
kurzer Druck → Tür öffnen
```

## Anschluss

```text
ESP32 GPIO 18 → Taster → GND
```

Mit internem Pullup:

```text
nicht gedrückt = HIGH
gedrückt     = LOW
```

Position:

```text
außen am Technikfach oder geschützt unter dem Deckel
```

---

# IR-Lichtschranken

## Zweck

```text
Erkennen, ob Kopf, Pfote oder Körper im Türbereich ist.
Blockiert → Tür darf nicht schließen.
```

## Pins

```text
Lichtschranke unten → GPIO 34
Lichtschranke oben  → GPIO 35
```

Achtung:

```text
GPIO 34/35 haben keine internen Pullups.
Wenn das Sensor-Modul keinen definierten Ausgang liefert, externe Pullups/Pulldowns einplanen.
```

## Logik

Je nach Modul:

```text
frei      = HIGH oder LOW
blockiert = LOW oder HIGH
```

Darum im Code konfigurierbar machen:

```text
LIGHT_BARRIER_ACTIVE_LOW = true/false
```

---

# Wichtig bei 5V-Lichtschranken

Wenn die Lichtschranken mit 5V laufen und am Ausgang 5V liefern:

```text
Nicht direkt auf ESP32 GPIO 34/35 geben.
```

Dann nötig:

```text
- Spannungsteiler
oder
- Level-Shifter
oder
- 3,3V-kompatible Lichtschranken verwenden
```

Empfehlung:

```text
möglichst 3,3V-kompatible Sensoren kaufen
oder digitale Module mit Open-Collector-Ausgang verwenden.
```

---

# RGB-LED / Status-LED

## Pins

```text
Rot  → GPIO 19
Grün → GPIO 23
Blau → GPIO 5
```

Jeder LED-Kanal braucht einen Vorwiderstand.

```text
typisch 220–330 Ohm je Kanal
```

Bei fertigem RGB-LED-Modul prüfen, ob Widerstände bereits vorhanden sind.

## Statusfarben geplant

```text
Grün: richtige Katze erkannt / Tür offen
Rot kurz: falscher Tag
Blau: Tür bewegt sich
Gelb: blockiert / wartet
Rot blinkend: Fehler
```

---

# Hauptschalter

Der Hauptschalter sitzt in der 12V-Zuleitung nach Sicherung oder kombiniert mit Netzteil-Eingang.

```text
+12V Netzteil → Sicherung → Hauptschalter → System +12V
```

Funktion:

```text
Box stromlos schalten.
```

---

# Sicherung

Empfohlen:

```text
2A Sicherung pro Box
```

Position:

```text
möglichst direkt nach dem 12V-Eingang
```

Zweck:

```text
Schutz bei Kurzschluss oder Fehler in der Box.
```

---

# Text-Schaltplan Übersicht

```text
                +12V Netzteil
                     │
                  Sicherung
                     │
                Hauptschalter
                     │
       ┌─────────────┴─────────────┐
       │                           │
       ▼                           ▼
 TB6612FNG VM                 Step-Down 5V
       │                           │
       ▼                           ▼
 12V Motor                  ESP32 / Sensorik

Gemeinsamer GND überall verbunden.
```

---

# Signalübersicht

```text
ESP32 GPIO 21/22  → I2C: PN532 + VL53L0X
ESP32 GPIO 25/26/27/14 → TB6612FNG Motorsteuerung
ESP32 GPIO 32     → Endschalter offen
ESP32 GPIO 33     → Endschalter geschlossen
ESP32 GPIO 34     → Lichtschranke unten
ESP32 GPIO 35     → Lichtschranke oben
ESP32 GPIO 18     → Notfall-Taster
ESP32 GPIO 19/23/5 → RGB-LED
```

---

# Steckverbinder-Empfehlung

Für den finalen Aufbau sollten Baugruppen steckbar sein.

## Türmodul-Stecker

```text
Motor + Endschalter offen + Endschalter zu
```

## Sensorrahmen-Stecker

```text
Lichtschranke unten + Lichtschranke oben
```

## RFID-Stecker

```text
VCC, GND, SDA, SCL
```

## Innensensor-Stecker

```text
VCC, GND, SDA, SCL
```

Vorteil:

```text
Reparatur und Austausch ohne Abschneiden von Kabeln.
```

---

# Prototyp-Testreihenfolge

## Test 1: Strom

```text
[ ] 12V Netzteil liefert stabile Spannung.
[ ] Step-Down ist auf 5V eingestellt.
[ ] ESP32 startet über 5V.
[ ] GND überall gemeinsam.
```

## Test 2: I2C

```text
[ ] PN532 wird erkannt.
[ ] VL53L0X wird erkannt.
[ ] I2C-Scanner zeigt beide Geräte.
```

## Test 3: Eingänge

```text
[ ] Endschalter offen wird erkannt.
[ ] Endschalter geschlossen wird erkannt.
[ ] Notfall-Taster wird erkannt.
[ ] Lichtschranke unten frei/blockiert wird erkannt.
[ ] Lichtschranke oben frei/blockiert wird erkannt.
```

## Test 4: Motor

```text
[ ] Motor dreht Richtung öffnen.
[ ] Motor dreht Richtung schließen.
[ ] PWM ändert Geschwindigkeit.
[ ] STBY schaltet Treiber sauber ab.
```

## Test 5: Gesamtlogik ohne Katze

```text
[ ] richtiger RFID-Tag öffnet.
[ ] falscher RFID-Tag öffnet nicht.
[ ] Lichtschranke blockiert Schließen.
[ ] Blockade beim Schließen löst Wiederöffnen aus.
[ ] Endschalter stoppen Motor.
```

---

# Sicherheitsregeln beim Verkabeln

```text
- Netzteil erst einstecken, wenn Verdrahtung geprüft ist.
- Step-Down vor Anschluss an ESP32 auf 5V einstellen.
- Keine 5V-Signale auf ESP32-GPIOs.
- Motor nicht direkt an ESP32 anschließen.
- GND gemeinsam verbinden.
- Kabel gegen Zug sichern.
- Keine offenen Kontakte im Katzenraum.
- Finale Box nicht mit Breadboard betreiben.
```

---

# Offene Punkte vor finalem Einkauf

```text
- konkretes ESP32-Modell
- konkretes PN532-Modul und Betriebsspannung
- konkrete Lichtschranken und Ausgangspegel
- konkretes VL53L0X-Breakout und Betriebsspannung
- konkreter TB6612FNG-Treiber
- Steckverbindertypen
- Sicherungshalter
- Hauptschaltertyp
- RGB-LED-Modul oder einzelne LED
```

---

# Ergebnis Zeichnungspaket 06

Gesetzt ist:

```text
- pro Box eigener ESP32
- 12V/2A Netzteil pro Box
- Step-Down 12V auf 5V
- PN532 und VL53L0X über I2C
- TB6612FNG für 12V-Motor
- Endschalter und Taster gegen GND mit Pullup
- zwei Lichtschranken an GPIO 34/35
- Status-LED optional über GPIO 19/23/5
- gemeinsame Masse für alle Baugruppen
- keine 5V-Signale direkt auf ESP32-GPIOs
```

---

# Nächstes Dokument

Als nächstes sollte ein Bau- und Testplan erstellt werden:

```text
- Reihenfolge der Holzarbeiten
- Reihenfolge der Mechaniktests
- Reihenfolge der Elektroniktests
- erste Inbetriebnahme
- Trainingsmodi mit Katzen
```
