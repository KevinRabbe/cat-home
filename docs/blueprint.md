# Cat Home Blueprint

Diese Datei ist die zentrale Blaupause für das RFID-Katzen-Futterhaus.

## Gesetzte Grundentscheidungen

- Zwei getrennte Boxen: eine Box pro Katze.
- Eine Standardbox für die kleinere/Bengal-Mix-Katze.
- Eine größere Largebox für die Maine-Coon-Katze.
- RFID/NFC-Tags am Halsband, keine implantierten Tierchips.
- Pro Box eigene Elektronik.
- Pro Box eine seitliche Schiebetür.
- Türantrieb über 12V-Getriebemotor, nicht über Servo.
- Sensorik verhindert Einklemmen.
- Katze muss von innen immer raus können.
- Oben kompletter Klappdeckel mit Scharnieren.
- Innen erhöhte Futterplattform mit zwei Kerbl-Edelstahlnäpfen.
- Futtereinsatz herausnehmbar und leicht zu reinigen.

---

# Modul 1: Grundbox + Innenaufteilung

## Standardbox

- Außenmaß: 100 x 60 x 60 cm
- Eingang: 25 x 30 cm
- Futterpodest: 38 x 38 x 10 cm
- Liegefläche: ca. 45–50 x 40 cm
- Schiebetür: ca. 32 x 36 cm

## Largebox / Maine Coon

- Außenmaß: 120 x 65 x 65 cm
- Eingang: 30 x 35 cm
- Futterpodest: 42 x 42 x 10–12 cm
- Liegefläche: mindestens 60 x 45 cm
- Schiebetür: ca. 37 x 42 cm

## Aufbau

- Bodenplatte
- Rückwand
- zwei Seitenwände
- Frontwand
- kompletter Klappdeckel oben
- Lüftungsschlitze oder Bohrungen oben/hinten/seitlich
- separates Technikfach empfohlen

## Innenzonen

- Vorne: Eingangs-/Türbereich
- Hinten links: Liege-/Chillbereich
- Hinten rechts: Futterbereich mit erhöhtem Podest
- Zwischen Liege- und Futterbereich: kleine Trennkante

---

# Modul 2: Futterpodest + herausnehmbarer Einsatz

## Ziel

Der Futterbereich soll erhöht, leicht zu reinigen und gegen Verrutschen gesichert sein.

## Standardbox

- Podest: 38 x 38 x 10 cm
- Herausnehmbarer Einsatz: ca. 37,5 x 37,5 cm

## Largebox

- Podest: 42 x 42 x 10–12 cm
- Herausnehmbarer Einsatz: passend etwas kleiner als das Podest

## Näpfe

- Kerbl Edelstahlnapf 300 ml
- Pro Box: 2 eingebaut + 2 Ersatz
- Für beide Boxen insgesamt: 8 Näpfe

## Napf-Aussparungen

- Näpfe zuerst kaufen und real messen.
- Ausschnitt ca. 3–5 mm größer als der untere Napfkörper.
- Ausschnitt kleiner als oberer Napfrand, damit der Rand aufliegt.
- Griffkerbe neben jedem Napf einplanen.

## Einsatz-Fixierung

- Keine Magnete nötig.
- Dübel/Zapfen-System verwenden.
- Empfehlung: Dübel fest am Podest, passende Löcher im Einsatz.
- Zusätzlich: hinterer Anschlag und seitliche Führung.

## Reinigung

- Einsatz aus wasserfester/glatter Platte bauen.
- Rand am Einsatz: 2–3 cm.
- Futterzone von Liegezone durch ca. 6 cm Trennkante trennen.
- Keine offenen Holzfugen im Futterbereich.

---

# Modul 3: Eingang + Türöffnung + Frontaufbau

## Standardbox

- Frontplatte: 100 x 60 cm
- Eingang: 25 x 30 cm
- Unterkante Eingang: ca. 8 cm über Boden
- Schiebetür: ca. 32 x 36 cm
- Türtasche rechts: ca. 38 cm
- RFID-Position: seitlich am Eingang, ca. 18–22 cm über Boden

## Largebox

- Frontplatte: 120 x 65 cm
- Eingang: 30 x 35 cm
- Unterkante Eingang: ca. 8–10 cm über Boden
- Schiebetür: ca. 37 x 42 cm
- Türtasche rechts: ca. 45 cm
- RFID-Position: seitlich am Eingang, ca. 22–26 cm über Boden

## Frontprinzip

- Eingang vorne links oder leicht links-mittig.
- Tür fährt nach rechts in die Türtasche.
- Tür läuft innen hinter der Front.
- Eingangsecken abrunden, Radius ca. 2–4 cm.
- Untere Schwelle 8–10 cm hoch, Kanten abrunden.

---

# Modul 4: Schiebetür + Mechanik + Motorantrieb

## Türtyp

- Seitliche Schiebetür.
- Läuft innen hinter der Front.
- Öffnet nach rechts.

## Türmaterial

- Standardbox: 3–4 mm Sperrholz.
- Largebox: 4–5 mm Sperrholz.

## Führung

- Obere und untere Kunststoff-U-Schiene.
- Schienen sauber ausrichten.
- Tür muss per Hand sehr leicht laufen.
- Anschläge mit Moosgummi/Filz/Silikonpuffer dämpfen.
- Schließkante weich ausführen.

## Antrieb

- 12V DC Getriebemotor, ca. 30 RPM.
- TB6612FNG Motortreiber.
- Geschlossene Schnurschleife oder später Zahnriemen.
- Für Version 1: Schnurschleife.
- Schnur: nicht elastisch, z. B. Nylon/Polyester/Dyneema.

## Endpositionen

- 1 Endschalter für Tür komplett offen.
- 1 Endschalter für Tür komplett geschlossen.
- Endschalter nicht als harte mechanische Anschläge missbrauchen.

## Zielgeschwindigkeit

- Öffnen: ca. 2–4 Sekunden.
- Schließen: ca. 2–4 Sekunden.

---

# Modul 5: Sensorik + Sicherheitslogik

## Sensoren pro Box

- 1x PN532 RFID/NFC-Leser außen.
- 2x IR-Lichtschranke im Eingang.
- 1x Innensensor zum Rauslassen, z. B. VL53L0X.
- 2x Endschalter für Tür offen/geschlossen.
- 1x Notfall-Taster empfohlen.
- 1x Status-LED empfohlen.

## Standardbox Sensorpositionen

- RFID: seitlich am Eingang, 18–22 cm über Boden.
- Lichtschranke unten: 16–18 cm über Boxboden.
- Lichtschranke oben: 28–31 cm über Boxboden.
- Innensensor: innen über/seitlich am Eingang, Erkennung ca. 10–35 cm vor der Tür.

## Largebox Sensorpositionen

- RFID: seitlich am Eingang, 22–26 cm über Boden.
- Lichtschranke unten: 18–22 cm über Boxboden.
- Lichtschranke oben: 33–38 cm über Boxboden.
- Innensensor: innen über/seitlich am Eingang, Erkennung ca. 10–45 cm vor der Tür.

## Sicherheitsregeln

- Tür schließt nie, wenn eine Lichtschranke blockiert ist.
- Tür öffnet immer, wenn der Innensensor eine Katze am Ausgang erkennt.
- Bei Blockade während des Schließens: Motor stoppen und wieder öffnen.
- Motor läuft nie ohne Timeout.
- Bei Fehler: Motor aus, Tür nicht hart schließen.
- Im Zweifel offen lassen.

---

# Modul 6: Elektronik + Stromversorgung + Verkabelung

## Pro Box

- 1x ESP32 Dev Board.
- 1x PN532 RFID/NFC Modul.
- 1x 12V DC Getriebemotor ca. 30 RPM.
- 1x TB6612FNG Motortreiber.
- 1x VL53L0X Innensensor.
- 2x IR-Lichtschranke.
- 2x Endschalter.
- 1x 12V / 2A Netzteil.
- 1x Step-Down-Wandler 12V auf 5V.
- 1x Hauptschalter.
- 1x Notfall-Taster.
- 1x Status-LED oder RGB-LED.
- 1x kleine Sicherung empfohlen.

## Stromversorgung

- Pro Box eigenes 12V/2A-Netzteil empfohlen.
- 12V direkt zum Motortreiber/Motor.
- 12V über Step-Down auf 5V für ESP32/Sensoren.
- Alle GND gemeinsam verbinden.
- Keine 5V-Signale direkt auf ESP32-GPIOs geben.

## Technikfach

- Elektronik separat vom Katzenraum.
- Keine losen Kabel im Katzenraum.
- Kabel durch Bohrungen/Kabelkanäle führen.
- Zugentlastung am Netzteilkabel.
- Steckbare Baugruppen bevorzugen.

## Vorläufiger ESP32-Pinplan

- I2C SDA: GPIO 21
- I2C SCL: GPIO 22
- Motor AIN1: GPIO 25
- Motor AIN2: GPIO 26
- Motor PWM: GPIO 27
- Motor STBY: GPIO 14
- Endschalter offen: GPIO 32
- Endschalter geschlossen: GPIO 33
- Lichtschranke unten: GPIO 34
- Lichtschranke oben: GPIO 35
- Notfall-Taster: GPIO 18
- RGB Rot: GPIO 19
- RGB Grün: GPIO 23
- RGB Blau: GPIO 5

---

# Modul 7: Software-Logik + Zustandsmaschine

## Zustände

- LOCKED
- OPENING
- OPEN
- WAITING_CLEAR
- CLOSING
- BLOCKED
- ERROR

## Kernlogik

- Richtiger RFID-Tag außen: Tür öffnet.
- Falscher RFID-Tag außen: Tür bleibt zu.
- Innensensor aktiv: Tür öffnet immer.
- Lichtschranke blockiert: Tür schließt nicht.
- Blockade während Schließen: Motor stoppt und Tür öffnet wieder.
- Endschalter stoppen Motor an Endpositionen.
- Timeout verhindert endlosen Motorlauf.
- Fehlerzustand: Motor aus, sicherer Zustand.

## Zeitwerte Startvorschlag

- clearDelay: 2500 ms
- maxOpeningTime: 6000 ms
- maxClosingTime: 6000 ms
- reopenPause: 300 ms
- rfidCooldown: 1000 ms
- sensorLoopDelay: 20–50 ms

## Trainingsmodi

- Modus 0: Sensorwerte anzeigen, Tür bewegt sich nicht.
- Modus 1: Tür bleibt offen, RFID wird nur geloggt.
- Modus 2: Richtiger Tag öffnet, Tür schließt nicht automatisch.
- Modus 3: Vollautomatik.

---

# Offene spätere Module

- Finale Stückliste mit Mengen und Preisen.
- Detaillierte Holz-Zuschnittliste.
- ESP32-Code.
- Testplan mit Katzen-Training.
- Wartungs- und Reinigungskonzept.
