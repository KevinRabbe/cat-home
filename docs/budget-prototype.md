# Budget-Prototyp – RFID-Eingang mit Halsbandchip

Ziel: Eine günstige erste Version bauen, die nur beweist, dass der Eingang per RFID/NFC-Halsbandtag zuverlässig öffnet und schließt.

Diese Version ist kein finaler Holzbau, sondern ein funktionaler Testaufbau.

---

# Hauptidee

Nicht direkt die komplette Katzen-Suite bauen.

Stattdessen zuerst:

```text
Karton-/Schaumplattenbox
+ RFID-Eingang
+ leichte Tür
+ einfacher Antrieb
+ versteckte Mechanik
```

Ziel:

```text
richtiger Halsbandchip → Tür öffnet
falscher Chip → Tür bleibt zu
Katze kann durch den Eingang
Mechanik ist für Katze nicht erreichbar
```

---

# Minimaler Budget-Aufbau

## Material für den Körper

Geeignet:

```text
- stabiler Karton
- Foamboard / Kapa-Platte
- dünne Sperrholzreste
- Kunststoffplatte
```

Für die erste Version reicht Karton, wenn er gut verstärkt wird.

Empfehlung:

```text
Frontplatte aus doppeltem Karton oder Foamboard
Tür aus leichtem Karton/Kunststoff
Kanten mit Gewebeband/Panzertape verstärken
```

---

# Wichtigste Sicherheitsregel

Auch beim Karton-Prototyp gilt:

```text
Katze darf keine Schnüre, Drähte, Kabel, Motoren oder Elektronik erreichen.
```

Mechanik muss verdeckt sein.

Empfohlene Bauform:

```text
Außenfront
↓
verdeckter Türkanal mit Mechanik
↓
Innenblende
↓
Katzenraum
```

Von innen sieht die Katze nur:

```text
glatte Öffnung
leichte Türfläche
keine Kabel
keine Schnur
keinen Servo
keine Rollen
```

---

# Türmechanik für Budget-Version

## Variante A – einfachste Version: Servo + leichte Schiebetür

Diese Variante ist für Karton am besten.

```text
ESP32 → Servo → Hebel/Stange → leichte Schiebetür
```

Vorteile:

```text
billig
einfach
wenige Teile
leicht zu programmieren
für Kartontür genug Kraft
```

Nachteile:

```text
Servo kann etwas surren
nicht so professionell wie Getriebemotor
für finale Holzbox eher nicht ideal
```

Für den Budget-Prototyp ist Servo trotzdem die beste Wahl.

---

## Empfohlener Servo

Nicht den allerschwächsten nehmen, wenn möglich.

Geeignet:

```text
MG90S Metallgetriebe-Servo
oder ähnlicher kleiner 5V Servo
```

Für sehr leichte Kartontür kann auch ein SG90 reichen, aber MG90S ist robuster.

---

# Türform

Empfohlen:

```text
seitliche Schiebetür aus leichtem Karton/Foamboard/Kunststoff
```

Nicht empfohlen:

```text
schwere Holzklappe
fallende Klappe nach unten
harte Tür mit viel Kraft
```

Die Tür soll leicht sein, damit bei Fehler wenig Kraft entsteht.

---

# Verdeckter Türkanal aus Karton

Die Front kann aus zwei Lagen bestehen:

```text
Lage 1: Außenfront mit Eingangsausschnitt
Lage 2: Abstandshalter / Türkanal
Lage 3: Innenblende mit gleichem Eingangsausschnitt
```

Die Tür läuft zwischen Lage 1 und Lage 3.

```text
Außenfront
[ Tür läuft im Zwischenraum ]
Innenblende
```

Dadurch kommt die Katze nicht an die Mechanik.

---

# 3D-druckbare Teile

3D-Druck ist für den Prototyp sehr sinnvoll.

Mögliche Druckteile:

```text
- U-Schienen für die leichte Schiebetür
- Servo-Halter
- Servoarm-Verlängerung
- kleine Türführung
- Sensorhalter
- RFID-Halter am Eingang
- Halter für Endanschläge
- Halsbandtag-Halter
```

Für Version 1 kann vieles auch aus Karton/Heißkleber gebaut werden, aber 3D-Druck macht es sauberer und wiederholbarer.

---

# Minimal-Elektronik für Budget-Prototyp

## Pflichtteile

```text
1x ESP32
1x PN532 RFID/NFC-Modul
1x NFC-Halsbandtag
1x kleiner Servo, z. B. MG90S
1x 5V-Netzteil oder USB-Netzteil
Kabel
Karton/Foamboard
Tape/Heißkleber
```

Damit geht schon:

```text
richtiger Tag erkannt → Tür öffnet
nach Zeit X → Tür schließt wieder
```

Aber diese Minimalversion hat noch keinen Einklemmschutz.

---

# Bessere Budget-Version mit Sicherheit

Empfohlen zusätzlich:

```text
1x IR-Lichtschranke oder einfacher Abstandssensor
1x Notfall-Taster
1x Status-LED
```

Dann geht:

```text
Tür schließt nur, wenn Eingang frei ist.
Wenn Sensor blockiert: Tür bleibt offen.
```

---

# Budget-Versionen

## V0 – RFID-Test auf dem Tisch

Ziel:

```text
ESP32 erkennt PN532.
Halsbandtag wird gelesen.
Tag-ID wird im seriellen Monitor angezeigt.
```

Teile:

```text
ESP32
PN532
NFC-Tag
USB-Kabel
```

Keine Tür.

---

## V1 – Karton-Tür ohne Katze

Ziel:

```text
richtiger Tag → Servo öffnet Kartontür
falscher Tag → Servo bleibt zu
Tür schließt nach Zeit wieder
```

Teile:

```text
ESP32
PN532
Servo
Kartonfront
leichte Schiebetür
Tape/Heißkleber
```

Nur mit Hand/Testobjekt testen, noch nicht mit Katze.

---

## V2 – Karton-Tür mit Einklemmschutz

Ziel:

```text
Tür schließt nur, wenn Eingang frei ist.
Sensor blockiert → Tür bleibt offen.
Blockade beim Schließen → Tür öffnet wieder.
```

Zusatzteile:

```text
IR-Lichtschranke oder VL53L0X
Notfall-Taster
Status-LED
```

Das ist die erste Version, die man vorsichtig mit Katzen trainieren kann.

---

## V3 – mechanisch sauberer Test mit 3D-Druckteilen

Ziel:

```text
gleiche Logik wie V2,
aber bessere Führungen und Halter.
```

Zusatz:

```text
3D-gedruckte U-Schienen
3D-gedruckter Servo-Halter
3D-gedruckte Sensorhalter
3D-gedruckter RFID-Halter
```

Diese Version kann später als Vorlage für Holzbau dienen.

---

# Grobe Budget-Schätzung

Ohne Holz und ohne Spezialwerkzeug:

```text
V0 RFID-Test:              ca. 15–30 €
V1 Karton-Tür:             ca. 25–45 €
V2 mit einfachem Sensor:   ca. 35–60 €
V3 mit 3D-Druckteilen:     ca. 45–90 €
```

Die Preise hängen stark davon ab, ob Teile als Set gekauft werden und ob bereits Kabel/Netzteile vorhanden sind.

---

# Warum Budget-Prototyp sinnvoll ist

Er testet die wichtigsten Risiken billig:

```text
- Wird der Halsbandtag zuverlässig erkannt?
- Akzeptiert die Katze den Eingang?
- Ist die Türbewegung zu laut?
- Ist die RFID-Position richtig?
- Reicht eine einfache Mechanik?
- Reagiert die Katze auf die Tür panisch oder entspannt?
```

Erst danach lohnt sich der große Holzbau.

---

# Empfohlene Reihenfolge

```text
1. V0: RFID auf dem Tisch testen.
2. Tag-ID jeder Katze speichern.
3. V1: Kartonfront mit leichter Schiebetür bauen.
4. Servo langsam öffnen/schließen lassen.
5. V2: Sensor einbauen, damit Tür nicht schließt wenn blockiert.
6. Mechanik komplett verdecken.
7. Mit Leckerli trainieren, Tür zuerst offen lassen.
8. Erst nach erfolgreichem Test in Holz übernehmen.
```

---

# Nicht verhandelbare Sicherheitsregel

Auch im Budget-Prototyp:

```text
Keine erreichbaren Schnüre.
Keine erreichbaren Kabel.
Keine erreichbare Elektronik.
Keine offene Mechanik im Katzenraum.
```

Wenn Karton verwendet wird, muss die Katze trotzdem nicht an die Steuerung kommen.
