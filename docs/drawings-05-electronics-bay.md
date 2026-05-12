# Zeichnungspaket 05 – Technikfach + Elektronikposition + Kabeldurchführungen

Dieses Dokument beschreibt das Technikfach, die räumliche Positionierung der Elektronik, Kabelwege und sichere Trennung zwischen Katzenraum und Elektronik.

Status: Planungsstand / erste Blaupause. Exakte Maße hängen von den real gekauften Komponenten und der finalen Boxkonstruktion ab.

---

# Ziel dieses Zeichnungspakets

Das Technikfach soll:

- Elektronik sicher vom Katzenraum trennen
- Wartung einfach machen
- Kabel sauber führen
- Motor, Sensoren und Steuerung sinnvoll verbinden
- Netzteil, Step-Down, ESP32 und Motortreiber aufnehmen
- keine losen Kabel im Katzenraum zulassen
- leicht zugänglich bleiben

---

# Gesetzte Entscheidungen

- Pro Box eigene Elektronik.
- Technikfach getrennt vom Katzenraum.
- Keine offenen Kontakte im Katzenraum.
- Keine losen Kabel im Katzenraum.
- Kabeldurchführungen mit Schutz/Entlastung.
- Montageplatte im Technikfach empfohlen.
- Hauptschalter pro Box empfohlen.
- Notfall-Taster pro Box empfohlen.
- Status-LED außen sichtbar empfohlen.
- Tür muss bei Stromausfall/manuell prüfbar bleiben.

---

# Zeichnungslegende

```text
TF   = Technikfach
MP   = Montageplatte
PSU  = 12V Netzteil / Stromzufuhr
SD   = Step-Down 12V → 5V
ESP  = ESP32
DRV  = TB6612FNG Motortreiber
RFID = PN532 RFID/NFC Modul
M    = 12V Getriebemotor
LB   = Lichtschranke
TOF  = VL53L0X Innensensor
ES   = Endschalter
SW   = Hauptschalter
BTN  = Notfall-Taster
LED  = Status-LED
```

---

# Grundprinzip

Die Elektronik sitzt nicht offen im Katzenraum, sondern in einem separaten Technikfach.

```text
┌──────────────────────── Katzenraum ────────────────────────┐
│                                                             │
│  Liegefläche             Futterbereich                      │
│                                                             │
│  Eingang / Türbereich                                       │
└───────────────────────────────────────────┬─────────────────┘
                                            │
                                            │ Kabeldurchführung
                                            ▼
                                  ┌─────────────────┐
                                  │ Technikfach TF  │
                                  │ ESP / DRV / SD  │
                                  └─────────────────┘
```

---

# Position des Technikfachs

## Empfehlung

Das Technikfach sitzt außen seitlich oder hinten oben an der Box.

Bevorzugte Position:

```text
rechts außen nahe der Türtasche
```

Warum:

```text
- kurze Kabelwege zum Motor
- kurze Kabelwege zu Endschaltern
- kurze Kabelwege zu Lichtschranken
- gut erreichbar
- Katzen kommen nicht an Elektronik
```

---

# Technikfach – grobe Maße

## Box A – Standardbox

```text
Mindestmaß Technikfach:
ca. 20 x 15 x 8 cm
```

Besser:

```text
ca. 25 x 18 x 10 cm
```

## Box B – Largebox

```text
Mindestmaß Technikfach:
ca. 25 x 15 x 10 cm
```

Besser:

```text
ca. 30 x 20 x 10 cm
```

Grund:

```text
Elektronikfächer werden schnell zu eng.
Mehr Platz erleichtert Wartung und saubere Verkabelung.
```

---

# Technikfach – Draufsicht

Prinzip für beide Boxen:

```text
┌───────────────────────────────┐
│ Technikfach TF                │
│                               │
│ ┌─────────────┐ ┌───────────┐ │
│ │  MP         │ │ Kabel-    │ │
│ │ Montage-    │ │ durch-    │ │
│ │ platte      │ │ führung   │ │
│ └─────────────┘ └───────────┘ │
│                               │
│ SW   BTN   LED                │
└───────────────────────────────┘
```

---

# Montageplatte

Eine herausnehmbare oder gut zugängliche Montageplatte ist empfohlen.

## Funktion

Auf der Montageplatte sitzen:

```text
- ESP32
- TB6612FNG Motortreiber
- Step-Down-Wandler
- Klemmen/Stecker
- Sicherung
```

## Vorteil

```text
- Elektronik kann sauber aufgebaut werden.
- Wartung ist leichter.
- Weniger Kabelsalat.
- Komponenten sind nicht direkt auf der Boxwand verteilt.
```

---

# Montageplatte – Layoutvorschlag

```text
┌────────────────────────────────────┐
│ Montageplatte MP                   │
│                                    │
│  ┌────────┐    ┌──────────────┐    │
│  │ ESP32  │    │ TB6612FNG    │    │
│  └────────┘    └──────────────┘    │
│                                    │
│  ┌──────────────┐ ┌────────────┐   │
│  │ Step-Down SD │ │ Sicherung  │   │
│  └──────────────┘ └────────────┘   │
│                                    │
│  ┌──────────────────────────────┐  │
│  │ Klemmen / Steckverbinder     │  │
│  └──────────────────────────────┘  │
└────────────────────────────────────┘
```

---

# Stromversorgung

## Pro Box

```text
12V / 2A Netzteil
```

Verschaltung:

```text
12V Eingang
  │
  ├── Sicherung 2A empfohlen
  │
  ├── Hauptschalter SW
  │
  ├── 12V → TB6612FNG / Motorversorgung
  │
  └── 12V → Step-Down 5V → ESP32/Sensorik
```

---

# Gemeinsame Masse

Alle GND müssen verbunden sein.

```text
GND Netzteil
GND Step-Down
GND ESP32
GND Motortreiber
GND Sensoren
GND RFID
GND Motorversorgung
```

Ohne gemeinsame Masse funktionieren Steuersignale nicht zuverlässig.

---

# 5V und 3,3V Sicherheit

Wichtig:

```text
ESP32 GPIOs sind 3,3V-Logik.
Keine 5V-Signale direkt auf ESP32-Eingänge geben.
```

Sichere Varianten:

```text
- Sensoren mit 3,3V-kompatiblem Ausgang nutzen.
- Endschalter/Taster gegen GND mit internem Pullup nutzen.
- Bei 5V-Signalen Spannungsteiler oder Level-Shifter verwenden.
```

---

# Kabeldurchführungen

Alle Kabel vom Katzenraum ins Technikfach sollen geschützt geführt werden.

## Anforderungen

```text
- kleine Bohrungen passend zur Leitung
- Kanten entgraten/schleifen
- Kabel nicht an scharfen Holzrändern führen
- optional Gummitülle/Kabeldurchführung verwenden
- Kabelzug entlasten
```

## Kabelgruppen

```text
1. Motorleitung
2. Endschalterleitungen
3. Lichtschrankenleitungen
4. RFID-Leitung
5. Innensensorleitung
6. LED/Taster-Leitungen
7. Stromzufuhr
```

---

# Kabelwege – Prinzip

```text
RFID außen am Eingang
    │
    └── Kabel durch Front/Seitenwand ins TF

Lichtschranken im Eingang
    │
    └── Kabel direkt seitlich ins TF

Motor in Türtasche
    │
    └── kurzes Kabel zum TB6612FNG im TF

Endschalter offen/zu
    │
    └── Kabel entlang Türtasche ins TF

Innensensor innen
    │
    └── Kabel geschützt durch Wand ins TF
```

---

# Katzenraum muss kabelfrei bleiben

Im Innenraum der Box sollen keine frei zugänglichen Kabel liegen.

Nicht erlaubt:

```text
- lose Dupont-Kabel im Katzenraum
- offene Kontakte
- Kabel entlang der Liegefläche
- Kabel nahe Näpfen/Futterbereich
```

Erlaubt / empfohlen:

```text
- Kabel hinter Abdeckung
- Kabel durch Wand direkt ins Technikfach
- Kabelkanal außerhalb des Katzenraums
- Sensoren bündig/geschützt montiert
```

---

# Bedienungselemente außen

## Hauptschalter SW

Funktion:

```text
Box stromlos schalten.
```

Position:

```text
außen am Technikfach
nicht direkt im Spielbereich der Katze
```

## Notfall-Taster BTN

Funktion:

```text
kurzer Druck → Tür öffnen
```

Position:

```text
außen oder unter dem oberen Klappdeckel
so, dass Menschen ihn gut erreichen, Katzen aber nicht ständig drücken
```

## Status-LED

Funktion:

```text
Status/Fehler sichtbar machen
```

Position:

```text
außen am Technikfach oder vorne seitlich
```

---

# Status-LED Vorschlag

```text
Grün: richtige Katze erkannt / Tür offen
Rot kurz: falscher Tag
Blau: Tür bewegt sich
Gelb: Sensor blockiert / wartet
Rot blinkend: Fehler
```

Für Version 1 reicht auch eine einfache LED, aber RGB erleichtert Debugging.

---

# RFID-Modul Position

Der PN532 sitzt außen am Eingang, aber sein Kabel geht ins Technikfach.

Wichtig:

```text
- RFID-Leser möglichst nahe am Halsbandtag.
- Halterung verstellbar planen.
- Kabel kurz und geschützt führen.
- RFID nicht direkt neben Motor oder dicken Motorkabeln montieren.
```

Grund:

```text
Motorstörungen können die Erkennung verschlechtern.
```

---

# Motor- und RFID-Abstand

Empfehlung:

```text
RFID am Eingang.
Motor eher rechts in der Türtasche / Technikfach.
Motorkabel nicht direkt parallel am RFID-Modul vorbeiführen.
```

Falls nötig:

```text
- Motorkabel verdrillen.
- Motor entstören.
- RFID-Kabel getrennt führen.
```

---

# Motorentstörung optional

Falls der Motor Störungen verursacht:

```text
- kleiner Kondensator direkt am Motor
- verdrillte Motorkabel
- getrennte Kabelführung von Signal- und Motorleitungen
```

Dies wird erst nötig, wenn beim Testen Probleme auftreten.

---

# Zugentlastung

Besonders wichtig bei:

```text
- Netzteilkabel
- Motorkabel
- Kabeln zur bewegten Türmechanik
```

Umsetzung:

```text
- Kabelbinderhalter
- kleine Klemme
- Kabeldurchführung mit Zugentlastung
- Kabel nicht direkt an Lötstelle/Klemme belasten
```

---

# Steckbare Baugruppen

Empfohlen für den finalen Aufbau:

```text
- Türmodul steckbar
- Sensorrahmen steckbar
- RFID-Modul steckbar
- Motor steckbar
- Bedienfeld steckbar
```

Vorteil:

```text
- Front kann entfernt werden.
- Sensor kann getauscht werden.
- Türmodul kann repariert werden.
- Elektronik lässt sich ohne Abschneiden ausbauen.
```

---

# Prototyp vs. finaler Aufbau

## Prototyp erlaubt

```text
- Breadboard
- Dupont-Kabel
- lose Testverkabelung außerhalb der Katzenbox
```

## Finale Box

```text
- keine Breadboards im Dauerbetrieb
- keine losen Dupont-Kabel im Katzenraum
- Schraubklemmen / JST / Wago / saubere Steckverbinder
- Schrumpfschlauch und Zugentlastung
```

---

# Technikfach Wartung

Das Technikfach sollte geöffnet werden können.

Möglichkeiten:

```text
- kleiner Deckel
- verschraubte Serviceklappe
- abnehmbare Abdeckung
```

Wichtig:

```text
- nicht dauerhaft verleimen
- ESP32-USB-Port erreichbar lassen, wenn möglich
- Reset/Flash sollte möglich bleiben
```

---

# Empfohlene Reihenfolge beim Aufbau

```text
1. Technikfach mechanisch planen.
2. Montageplatte zuschneiden.
3. ESP32, Motortreiber und Step-Down testweise platzieren.
4. Kabeldurchführungen planen.
5. Sensor- und Motorleitungen trocken verlegen.
6. Erst danach endgültige Bohrungen setzen.
7. Elektronik außerhalb der Box testen.
8. Dann ins Technikfach einbauen.
```

---

# Sicherheitsanforderungen

```text
- Netzteil und 12V-Bereich sauber isolieren.
- Keine offenen Metallkontakte.
- Keine frei zugänglichen Kabel im Katzenraum.
- Hauptschalter zugänglich.
- Sicherung empfohlen.
- Tür manuell bewegbar/prüfbar halten.
- Elektronik nicht direkt unter Nassfutterbereich montieren.
```

---

# Offene Punkte vor finalem Bau

Diese Punkte hängen von realen Teilen ab:

```text
- exakte Größe des ESP32-Boards
- exakte Größe des TB6612FNG-Moduls
- exakte Größe des Step-Down-Wandlers
- Größe der Klemmen/Stecker
- Netzteilart: externes Steckernetzteil oder internes Modul
- finale Position von Hauptschalter, Taster, LED
- exakte Kabeldurchführungen
- ob Technikfach seitlich oder hinten gebaut wird
```

---

# Ergebnis Zeichnungspaket 05

Gesetzt ist:

```text
- getrenntes Technikfach pro Box
- bevorzugt rechts außen nahe der Türtasche
- Montageplatte im Technikfach
- 12V/2A Netzteil pro Box
- Step-Down 12V auf 5V
- ESP32 + TB6612FNG + Klemmen auf Montageplatte
- Kabel geschützt durch Wand/Bohrungen führen
- Katzenraum bleibt kabelfrei
- Hauptschalter, Notfall-Taster und Status-LED empfohlen
- steckbare Baugruppen bevorzugt
```

---

# Nächstes Zeichnungspaket

Zeichnungspaket 06 sollte den Verdrahtungsplan beschreiben:

```text
- ESP32-Pinplan
- PN532-I2C
- VL53L0X-I2C
- TB6612FNG-Anschluss
- Endschalter
- Lichtschranken
- Notfall-Taster
- Status-LED
- Stromverteilung 12V/5V/3,3V
```
