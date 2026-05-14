# Low-Budget Build Guide – Maine-Coon RFID-Kartonbox

Ziel: Eine möglichst günstige, funktionierende Testversion bauen, bei der nur die Maine Coon per NFC/RFID-Halsbandtag Zugang zu einer Kartonbox bekommt.

Diese Anleitung ist so geschrieben, dass man nach dem Bestellen der Teile Schritt für Schritt vorgehen kann.

---

# 0. Ziel der ersten Version

Diese Version soll beweisen:

```text
- Der Halsbandchip wird zuverlässig erkannt.
- Die Tür öffnet nur bei richtigem Tag.
- Die Tür bleibt offen, wenn der Eingang blockiert ist.
- Die Katze kommt sicher rein und raus.
- Die Katze akzeptiert die Box.
```

Diese Version muss noch nicht schön sein.

Sie muss aber sicher sein.

---

# 1. Finale Minimal-Teileliste

## Pflichtteile kaufen

| Teil | Menge | Suchbegriff | Zweck |
|---|---:|---|---|
| ESP32 Dev Board | 1 | `ESP32 DevKit USB-C` | Steuerung |
| PN532 NFC/RFID Modul | 1 | `PN532 NFC RFID Modul I2C SPI UART` | Halsbandtag lesen |
| NFC-Tag / Schlüsselanhänger | 1–2 | `NFC Schlüsselanhänger NTAG213` | Chip am Halsband |
| Sicherheits-Katzenhalsband | 1 | `Katzenhalsband Sicherheitsverschluss` | Tag tragen |
| MG90S Servo | 1 | `MG90S Servo Metallgetriebe` | leichte Tür bewegen |
| IR-Lichtschranke | 1 | `IR Lichtschranke Modul Arduino` | Einklemmschutz |
| Notfall-Taster | 1 | `Drucktaster Arduino momentary` | Tür manuell öffnen |
| Jumper-Kabel Set | 1 | `Dupont Kabel Set Arduino` | Verkabelung |

## Wenn nicht vorhanden

| Teil | Menge | Suchbegriff | Zweck |
|---|---:|---|---|
| USB-Netzteil 5V / 2A | 1 | `USB Netzteil 5V 2A` | Stromversorgung |
| USB-Kabel für ESP32 | 1 | passend zum ESP32 | Strom + Programmieren |
| Foamboard 5 mm | optional | `Foamboard 5mm` | stabiler als Karton |
| Gewebeband/Panzertape | 1 Rolle | `Gewebeband stark` | Verstärkung |
| Heißkleber/Kleber | nach Bedarf | `Heißklebesticks` | Kartonbau |
| Wago/Lüsterklemmen | optional | `Wago 221 Klemmen` | Kabel verbinden |

## Vorhanden / nicht kaufen

```text
- vorhandene Näpfe
- vorhandene Silikonmatte
- Karton, falls stabil genug vorhanden
- altes USB-Netzteil, falls 5V/2A vorhanden
- alte Niedervolt-Kabel, falls vorhanden
```

---

# 2. Budget-Erwartung

Wenn Karton, USB-Netzteil, Kabel, Tape und Kleber vorhanden sind:

```text
ca. 25–50 €
```

Wenn fast alles gekauft werden muss:

```text
ca. 35–70 €
```

---

# 3. Sicherheitsregeln vor Start

Nicht verhandelbar:

```text
Keine 230V-Bastelei.
Nur mit 5V nach dem USB-Netzteil arbeiten.
Keine sichtbaren Kabel im Katzenraum.
Keine offene Servo-Mechanik im Katzenraum.
Keine erreichbare Schnur oder Hebel im Katzenraum.
Tür muss leicht sein.
Tür schließt nur, wenn Sensor frei ist.
Bei Unsicherheit bleibt die Tür offen.
```

Wichtig:

```text
Alles vor dem USB-Netzteil / Steckdose ist tabu.
Alles nach dem USB-Netzteil ist 5V und für den Prototyp geeignet.
```

---

# 4. Grundaufbau der Kartonbox

## Empfohlene Boxgröße für Maine Coon

Für einen echten Box-Test:

```text
Breite:  60–80 cm
Tiefe:   50–60 cm
Höhe:    50–60 cm
Eingang: ca. 30 x 35 cm
```

Für den allerersten Türtest reicht auch nur eine Frontplatte:

```text
Kartonfront mit Eingang
Türmodul
keine komplette Box
```

---

# 5. Schichten der Front

Die Front besteht aus drei Lagen:

```text
1. Außenfront mit Eingangsausschnitt
2. Zwischenraum = Türkanal + Servo/Mechanik
3. Innenblende mit gleichem Eingangsausschnitt
```

ASCII-Schnitt:

```text
Außen
│
├── Außenfront
├── Türkanal mit leichter Schiebetür + Servo
├── Innenblende / Schutzwand
│
Innenraum Katze
```

Ziel:

```text
Die Katze sieht innen nur eine glatte Öffnung.
Sie kommt nicht an Servo, Kabel oder Hebel.
```

---

# 6. Tür für Budget-Version

## Türmaterial

```text
leichter Karton
oder Foamboard
oder dünne Kunststoffplatte
```

Die Tür mit Tape verstärken:

```text
- Vorderkante verstärken
- Ober-/Unterkante verstärken
- Befestigungspunkt für Servo verstärken
```

## Türbewegung

Empfohlen:

```text
seitliche Schiebetür
Tür fährt nach rechts auf
Servo bewegt über kurzen Hebel oder Schubstange
```

Nicht verwenden:

```text
fallende Klappe
schwere Tür
Federmechanismus
offene Schnur im Innenraum
```

---

# 7. Sensorposition

Eine IR-Lichtschranke reicht für den ersten Prototyp.

Position:

```text
quer durch den Eingang
ungefähr mittig/unten im Durchgang
```

Empfohlen für Maine Coon:

```text
ca. 15–20 cm über Eingang-Unterkante
```

Logik:

```text
Strahl frei → Tür darf schließen
Strahl unterbrochen → Tür bleibt offen
```

---

# 8. RFID-Position

Der PN532 muss außen am Eingang sitzen, wo der Halsbandtag nah vorbeikommt.

Startposition:

```text
seitlich am Eingang
ca. 22–26 cm über Boden
```

Wichtig:

```text
Halterung nicht sofort endgültig verkleben.
Erst testen, ob der Tag zuverlässig erkannt wird.
```

---

# 9. Verkabelung – Minimalplan

## Strom

```text
USB-Netzteil 5V/2A
→ USB-Kabel
→ ESP32
```

Wenn Servo den ESP32 neu starten lässt:

```text
USB-5V aufteilen:
+5V → ESP32 5V/VIN
+5V → Servo VCC
GND → ESP32 GND
GND → Servo GND
```

Alle GND gemeinsam:

```text
ESP32 GND
PN532 GND
Servo GND
Lichtschranke GND
Taster GND
```

---

# 10. Pin-Vorschlag ESP32

Dieser Pinplan ist für die erste Version ausreichend.

```text
PN532 SDA  → GPIO 21
PN532 SCL  → GPIO 22
Servo Signal → GPIO 18
Lichtschranke Signal → GPIO 34
Notfall-Taster → GPIO 19
```

Strom:

```text
PN532 VCC → 3,3V oder 5V je nach Modul
PN532 GND → GND
Servo VCC → 5V
Servo GND → GND
Lichtschranke VCC → 3,3V oder 5V je nach Modul
Lichtschranke GND → GND
```

Achtung:

```text
ESP32 GPIOs vertragen nur 3,3V.
Wenn die Lichtschranke 5V-Signal ausgibt, Spannungsteiler oder 3,3V-kompatibles Modul nutzen.
```

---

# 11. Software-Zustände für Budget-Version

Minimal reichen diese Zustände:

```text
LOCKED
OPENING
OPEN
WAITING_CLEAR
CLOSING
ERROR
```

## Logik

```text
LOCKED:
  wartet auf richtigen RFID-Tag oder Notfall-Taster

OPENING:
  Servo öffnet Tür

OPEN:
  Tür bleibt offen, solange Lichtschranke blockiert ist

WAITING_CLEAR:
  Sensor ist frei, 2–3 Sekunden warten

CLOSING:
  Servo schließt langsam
  wenn Sensor blockiert → wieder öffnen

ERROR:
  Tür offen lassen, manuell prüfen
```

---

# 12. Reihenfolge beim Bauen

## Phase 1 – RFID auf dem Tisch

```text
[ ] ESP32 per USB anschließen.
[ ] PN532 anschließen.
[ ] Beispielcode / Testcode hochladen.
[ ] NFC-Tag an PN532 halten.
[ ] Tag-ID im seriellen Monitor ausgeben.
[ ] erlaubte Tag-ID notieren.
```

Ziel:

```text
Chip wird zuverlässig gelesen.
```

---

## Phase 2 – Servo einzeln testen

```text
[ ] Servo an 5V/GND/Signal anschließen.
[ ] Servo langsam zwischen offen/zu bewegen.
[ ] Offene Position bestimmen.
[ ] Geschlossene Position bestimmen.
[ ] Werte notieren.
```

Ziel:

```text
Servo bewegt sich kontrolliert und nicht ruckartig.
```

---

## Phase 3 – Lichtschranke testen

```text
[ ] Lichtschranke anschließen.
[ ] Seriellen Monitor nutzen.
[ ] Strahl frei/blockiert anzeigen.
[ ] Prüfen, ob Logik HIGH/LOW invertiert ist.
```

Ziel:

```text
Code erkennt zuverlässig frei/blockiert.
```

---

## Phase 4 – RFID + Servo kombinieren

```text
[ ] richtiger Tag → Servo öffnet
[ ] falscher Tag → Servo bleibt zu
[ ] Notfall-Taster → Servo öffnet
```

Noch ohne Tür.

---

## Phase 5 – Kartonfront bauen

```text
[ ] stabile Frontplatte zuschneiden.
[ ] Eingang ca. 30 x 35 cm ausschneiden.
[ ] Kanten mit Tape verstärken.
[ ] leichte Tür zuschneiden.
[ ] Türkanal mit Abstandshaltern bauen.
[ ] Innenblende bauen.
[ ] Tür per Hand schieben.
```

Ziel:

```text
Tür läuft leicht und klemmt nicht.
```

---

## Phase 6 – Servo mit Tür verbinden

```text
[ ] Servo im verdeckten Türkanal befestigen.
[ ] Servohebel mit Tür verbinden.
[ ] Öffnen/schließen ohne Katze testen.
[ ] Türbewegung langsam einstellen.
[ ] Mechanik verdecken.
```

Wichtig:

```text
Von innen darf die Katze nicht an Servo/Hebel/Kabel kommen.
```

---

## Phase 7 – Sensor in Front einsetzen

```text
[ ] Lichtschranke quer durch Eingang montieren.
[ ] Kabel direkt nach außen/ins Technikfach führen.
[ ] Sensor mit Hand testen.
[ ] Tür schließt nicht, wenn Hand im Eingang ist.
```

---

## Phase 8 – Gesamtlogik ohne Katze testen

```text
[ ] richtiger Tag öffnet Tür.
[ ] falscher Tag öffnet nicht.
[ ] Lichtschranke blockiert → Tür bleibt offen.
[ ] Lichtschranke frei → 2–3 Sekunden warten → Tür schließt.
[ ] während Schließen blockieren → Tür öffnet wieder.
[ ] Notfall-Taster öffnet immer.
```

Mindestens 30–50 Wiederholungen testen.

---

# 13. Katzentraining

## Stufe A – Box ohne Türbewegung

```text
Tür offen fixieren.
Näpfe + Silikonmatte rein.
Leckerli/Futter rein.
Katze freiwillig erkunden lassen.
```

Dauer:

```text
1–3 Tage oder länger, je nach Katze.
```

## Stufe B – RFID nur loggen

```text
Tür bleibt offen.
ESP32 liest Tag nur mit.
Prüfen, ob Tag am Halsband zuverlässig erkannt wird.
```

## Stufe C – Tür öffnet, schließt nicht automatisch

```text
Tür geschlossen.
richtiger Tag → Tür öffnet.
Tür bleibt offen.
```

## Stufe D – Automatisches Schließen aktivieren

Erst wenn Katze entspannt ist:

```text
Sensor frei
2–3 Sekunden warten
Tür langsam schließen
```

Wenn Katze Angst zeigt:

```text
zurück zu Stufe A oder B.
```

---

# 14. Abbruchkriterien

Automatik nicht benutzen, wenn:

```text
- Tür klemmt
- Servo ruckelt stark
- ESP32 startet neu
- Sensor erkennt nicht zuverlässig
- Katze hat sichtbar Angst
- Kabel/Mechanik erreichbar sind
- Tür schließt trotz blockiertem Eingang
```

Dann:

```text
Tür offen lassen und Fehler beheben.
```

---

# 15. Erfolgskriterien

Der Low-Budget-Prototyp gilt als erfolgreich, wenn:

```text
[ ] Tag wird in normaler Halsbandposition erkannt.
[ ] Tür öffnet zuverlässig.
[ ] Tür bleibt offen bei blockiertem Eingang.
[ ] Tür schließt langsam und sicher.
[ ] Katze akzeptiert die Box.
[ ] Mechanik bleibt verdeckt.
[ ] 3–7 Tage Testbetrieb ohne kritische Fehler möglich.
```

Erst danach lohnt sich der größere Holzbau.
