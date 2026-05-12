# Amazon-orientierte Teileliste pro Box

Status: Entwurf / Einkaufsvorbereitung.

Hinweis: Diese Liste ist als Amazon.de-orientierte Einkaufsliste gedacht. Amazon-Listings ändern sich häufig. Vor dem Kauf immer prüfen:

- Betriebsspannung
- Ausgangspegel 3,3V/5V
- Abmessungen
- Lieferumfang
- Bewertungen
- Lieferzeit
- Rückgabeoption

Bei Elektronik-Modulen sind viele Amazon-Angebote Marketplace-/No-Name-Angebote. Deshalb sind die technischen Spezifikationen wichtiger als der Markenname.

---

# Grundsatz pro Box

Jede Box bekommt eine eigene Elektronik:

```text
1x ESP32
1x RFID/NFC-Leser
1x Innensensor
2x Lichtschranke
1x Motor
1x Motortreiber
2x Endschalter
1x Stromversorgung
1x Technikfach-Verkabelung
```

Für zwei Boxen wird die Elektronik im Normalfall doppelt gekauft.

---

# 1. Futterbereich pro Box

| Teil | Menge pro Box | Menge für 2 Boxen | Amazon-Suchbegriff | Hinweis |
|---|---:|---:|---|---|
| Kerbl Edelstahlnapf 300 ml | 4 | 8 | `Kerbl Edelstahlnapf 300 ml` | 2 eingebaut + 2 Ersatz pro Box |
| Moosgummi/Silikonband dünn | 1 Rolle | 1–2 Rollen | `Moosgummi Dichtungsband selbstklebend 3mm` | gegen Klappern unter Napfrand/Tür |
| Kunststoff-/PVC-/HPL-Platte für Einsatz | 1 | 2 | `PVC Platte 3mm weiß schwarz Zuschnitt` | Futtereinsatz, leicht zu reinigen |
| Holzdübel/Zapfen | 2–4 | 4–8 | `Holzdübel 6mm 8mm` | Einsatz-Fixierung |

Notiz: Kerbl 300-ml-Näpfe müssen vor dem Sägen echt gemessen werden. Lochdurchmesser erst nach echtem Napfmaß festlegen.

---

# 2. Steuerung / Sensorik pro Box

| Teil | Menge pro Box | Menge für 2 Boxen | Amazon-Suchbegriff | Empfehlung |
|---|---:|---:|---|---|
| ESP32 Dev Board | 1 | 2 | `ESP32 DevKit C V4 USB-C` | lieber USB-C-Version kaufen |
| PN532 NFC/RFID Modul | 1 | 2 | `PN532 NFC RFID Modul I2C SPI UART` | muss 13,56 MHz Tags lesen können |
| NFC-Halsbandtag | 1–2 | 2–4 | `NFC Schlüsselanhänger 13.56MHz NTAG213` | pro Katze 1 Tag + Ersatz sinnvoll |
| VL53L0X ToF Sensor | 1 | 2 | `VL53L0X Time of Flight Sensor Arduino` | Innensensor zum Rauslassen |
| IR-Lichtschranke | 2 | 4 | `IR Lichtschranke Modul Arduino` | Einklemmschutz im Eingang |
| Endschalter/Mikroschalter | 2 | 4 | `Mikroschalter Endschalter Arduino` | Tür offen / Tür geschlossen |
| Notfall-Taster | 1 | 2 | `Drucktaster momentary Arduino` | manuelles Öffnen |
| RGB-LED oder LED-Modul | 1 | 2 | `RGB LED Modul Arduino` | Statusanzeige |

---

# 3. Motor / Türantrieb pro Box

## Variante A: leichter Motor, einfacher Treiber

| Teil | Menge pro Box | Menge für 2 Boxen | Amazon-Suchbegriff | Hinweis |
|---|---:|---:|---|---|
| kleiner 12V N20 Getriebemotor 30 RPM | 1 | 2 | `N20 Getriebemotor 12V 30RPM` | leise, klein, nur bei sehr leichtgängiger Tür |
| TB6612FNG Motortreiber | 1 | 2 | `TB6612FNG Motortreiber Modul` | reicht eher für kleine Motoren |

Diese Variante nur nehmen, wenn die Tür extrem leicht läuft.

## Variante B: kräftigerer Motor, robusterer Treiber – empfohlen für ersten echten Prototyp

| Teil | Menge pro Box | Menge für 2 Boxen | Amazon-Suchbegriff | Hinweis |
|---|---:|---:|---|---|
| 12V 30RPM Getriebemotor | 1 | 2 | `12V 30RPM Getriebemotor leise` | mehr Kraft für Schiebetür |
| DRV8871 Motortreiber oder vergleichbarer 3A+ DC-Motortreiber | 1 | 2 | `DRV8871 Motor Driver Modul` | robuster als TB6612 für stärkere Motoren |

Empfehlung: Für die finale Türmechanik lieber Variante B einplanen, weil sie mehr Reserve hat. Der TB6612FNG ist technisch sauber, aber je nach Motorstrom knapp.

---

# 4. Türmechanik pro Box

| Teil | Menge pro Box | Menge für 2 Boxen | Amazon-Suchbegriff | Hinweis |
|---|---:|---:|---|---|
| Kunststoff-U-Profil | 2 Stück / nach Länge | 4 Stück / nach Länge | `Kunststoff U Profil 5mm 6mm` | obere und untere Türführung |
| Nicht-elastische Schnur | ca. 1–2 m | ca. 2–4 m | `Dyneema Schnur 2mm` oder `Polyester Schnur 2mm` | Schnurschleife |
| kleine Umlenkrolle | 1–2 | 2–4 | `Mini Umlenkrolle 2mm Schnur` | für Schnurschleife |
| Moosgummi-/Silikonpuffer | nach Bedarf | nach Bedarf | `Gummipuffer selbstklebend Möbel` | leise Anschläge |
| Gummiprofil / Kantenschutz | nach Bedarf | nach Bedarf | `Gummi Kantenschutz U Profil` | weiche Schließkante |
| kleine Schrauben / Winkel / Ösen | nach Bedarf | nach Bedarf | `Schraubösen klein M3` | Schnurbefestigung |

Wichtig: Alle Schnüre, Rollen und Schienen müssen im fertigen Innenraum verdeckt sein. Katze darf nicht drankommen.

---

# 5. Stromversorgung / Verkabelung pro Box

| Teil | Menge pro Box | Menge für 2 Boxen | Amazon-Suchbegriff | Hinweis |
|---|---:|---:|---|---|
| 12V Netzteil 2A oder 3A | 1 | 2 | `12V 2A Netzteil Hohlstecker` | 3A gibt mehr Reserve |
| Step-Down 12V auf 5V | 1 | 2 | `LM2596 Step Down Modul` | ESP32/Sensorversorgung |
| DC-Buchse / Hohlsteckerbuchse | 1 | 2 | `DC Buchse 5.5 2.1mm Einbau` | Netzteileingang |
| Hauptschalter | 1 | 2 | `Wippschalter 12V Einbau` | Box stromlos schalten |
| Sicherungshalter + 2A Sicherung | 1 | 2 | `KFZ Sicherungshalter 2A` | Schutz empfohlen |
| WAGO 221 Set oder kleine Klemmen | 1 Set | 1 Set | `Wago 221 Set` | saubere Verteilung |
| JST-Stecker Set | 1 Set | 1 Set | `JST Stecker Set 2 Pin 3 Pin 4 Pin` | steckbare Module |
| Schrumpfschlauch Set | 1 Set | 1 Set | `Schrumpfschlauch Set` | Isolation |
| Litzenkabel Set | 1 Set | 1 Set | `Litzenkabel 0.25mm 0.5mm Set` | Sensoren/Strom |
| Kabelkanal klein | nach Bedarf | nach Bedarf | `Kabelkanal selbstklebend klein` | katzensichere Führung |

---

# 6. Holz-/Montagezubehör pro Box

Holz selbst ist vorhanden, aber diese Teile sind sinnvoll:

| Teil | Menge pro Box | Menge für 2 Boxen | Amazon-Suchbegriff | Hinweis |
|---|---:|---:|---|---|
| Scharniere für Deckel | 2–3 | 4–6 | `Möbelscharnier klein Edelstahl` | Klappdeckel oben |
| Kette / Deckelstütze | 1–2 | 2–4 | `Deckelstütze Truhe` oder `Kette verzinkt klein` | Deckel darf nicht zufallen |
| kleine Möbelgriffe / Griffmulden | optional | optional | `Griffmulde Möbel klein` | Serviceklappe / Einsatz |
| Einschlagmuttern / Gewindeeinsätze | optional | optional | `Gewindeeinsatz Holz M3 M4` | wartbare Schraubverbindungen |
| Holzschrauben Sortiment | 1 Set | 1 Set | `Holzschrauben Sortiment klein` | allgemeiner Aufbau |

---

# Mindest-Einkauf pro Box

Wenn man nur das kauft, was für Funktion nötig ist:

```text
1x ESP32 Dev Board
1x PN532 NFC/RFID Modul
1x NFC-Halsbandtag + Ersatz
1x VL53L0X Sensor
2x IR-Lichtschranke
2x Endschalter
1x 12V Getriebemotor
1x DRV8871 Motortreiber oder TB6612FNG bei kleinem Motor
1x 12V Netzteil 2–3A
1x LM2596 Step-Down
1x Notfall-Taster
1x Status-LED
Kabel/Klemmen/Stecker
2x Kerbl-Napf eingebaut + 2 Ersatz
Türschienen/Schnur/Umlenkrolle/Puffer
```

---

# Einkauf für beide Boxen

```text
2x ESP32
2x PN532
4x NFC-Halsbandtags empfohlen
2x VL53L0X
4x IR-Lichtschranken
4x Endschalter
2x 12V Getriebemotor
2x Motortreiber
2x 12V Netzteil
2x LM2596 Step-Down
2x Notfall-Taster
2x Status-LED
8x Kerbl Edelstahlnapf 300 ml
Schienen/Schnur/Umlenkrollen/Puffer für 2 Boxen
Kabel/Klemmen/Stecker als Set
```

---

# Noch offen vor Kauf

Vor dem Bestellen sollte entschieden werden:

```text
1. Leichter N20-Motor + TB6612FNG
oder
2. kräftigerer 12V-Getriebemotor + DRV8871/3A+ Motortreiber
```

Für den ersten echten Prototyp wird Variante 2 empfohlen, weil sie mehr Kraftreserve hat.

Außerdem prüfen:

```text
- Lichtschranken-Ausgang ist ESP32-kompatibel?
- PN532 unterstützt I2C und 13,56 MHz Tags?
- Step-Down vor Anschluss auf exakt 5V einstellen.
- Motorstrom passt zum Motortreiber.
```
