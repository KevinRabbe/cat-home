# Zeichnungspaket 04 – Schiebetür + Mechanik + Motorantrieb

Dieses Dokument beschreibt die seitliche Schiebetür, die Führungsschienen, die Türtasche, den Motorantrieb mit Schnurschleife, Endschalter und leise Anschläge.

Status: Planungsstand / erste mechanische Blaupause. Exakte Maße hängen von realen Schienen, Motor, Türmaterial und Holzstärke ab.

---

# Ziel dieses Zeichnungspakets

Die Türmechanik soll:

- leise öffnen und schließen
- zuverlässig laufen
- nicht verkanten
- günstig baubar sein
- wartbar bleiben
- bei Sensorblockade sofort stoppen können
- im stromlosen Zustand möglichst manuell bewegbar bleiben

---

# Gesetzte Entscheidungen

- Seitliche Schiebetür.
- Tür läuft innen hinter der Frontplatte.
- Tür öffnet nach rechts in eine Türtasche.
- Türmaterial: dünnes Sperrholz.
- Führung: obere und untere Kunststoff-U-Schiene.
- Antrieb: 12V DC Getriebemotor, ca. 30 RPM.
- Motortreiber später: TB6612FNG.
- Kraftübertragung: geschlossene Schnurschleife.
- Positionserkennung: 2 Endschalter.
- Anschläge: weich gedämpft mit Moosgummi/Filz/Silikonpuffer.

---

# Zeichnungslegende

```text
F  = Frontplatte
D  = Schiebetür / Door
E  = Eingang
T  = Türtasche
M  = Motor mit Antriebsrolle
U  = Umlenkrolle
S1 = Endschalter geschlossen
S2 = Endschalter offen
== = Schnurschleife
[] = U-Schiene / Führung
```

---

# Grundprinzip

## Geschlossen

```text
Frontansicht innen

┌────────────────────────────────────────────┐
│                                            │
│   [ D verdeckt Eingang E ]      T          │
│                                            │
└────────────────────────────────────────────┘
```

## Offen

```text
Frontansicht innen

┌────────────────────────────────────────────┐
│                                            │
│   [ Eingang E frei ]        [ D in T ]     │
│                                            │
└────────────────────────────────────────────┘
```

Die Tür fährt horizontal nach rechts.

---

# Box A – Standardbox

## Türdaten

```text
Eingang:      25 x 30 cm
Türplatte:    ca. 32 x 36 cm
Türmaterial:  3–4 mm Sperrholz
Türtasche:    ca. 38 cm rechts vom Eingang
Schienenlänge: ca. 70 cm
```

## Warum Tür größer als Eingang?

Die Tür muss den Eingang überlappen.

```text
Eingang:   25 x 30 cm
Tür:       32 x 36 cm
Überstand: ca. 3–4 cm seitlich, ca. 3 cm oben/unten
```

So wird der Eingang zuverlässig abgedeckt.

---

# Box B – Largebox / Maine Coon

## Türdaten

```text
Eingang:      30 x 35 cm
Türplatte:    ca. 37 x 42 cm
Türmaterial:  4–5 mm Sperrholz
Türtasche:    ca. 45 cm rechts vom Eingang
Schienenlänge: ca. 85 cm
```

## Warum größer?

Die Maine-Coon-Box braucht einen größeren Eingang und damit auch eine größere Türplatte mit Überlappung.

```text
Eingang:   30 x 35 cm
Tür:       37 x 42 cm
Überstand: ca. 3–4 cm seitlich, ca. 3–4 cm oben/unten
```

---

# Türführung mit U-Schienen

Die Tür läuft in einer oberen und einer unteren U-Schiene.

## Seiten-/Schnittansicht

```text
Frontplatte F
│
│   obere U-Schiene
│   ┌──────────────┐
│   │      D       │  ← dünne Schiebetür
│   └──────────────┘
│   untere U-Schiene
│
Innenraum
```

## Anforderungen

```text
- Schienen exakt parallel ausrichten.
- Tür darf nicht verkanten.
- Tür muss per Hand sehr leicht laufen.
- Keine Schraubenköpfe dürfen in der Laufbahn stehen.
- U-Schienen nicht zu eng wählen.
- Leichtes Spiel ist besser als Klemmen.
```

---

# Schienenmaterial

Empfohlen:

```text
Kunststoff-U-Profil
```

Warum:

```text
- leiser als Metall
- günstig
- leicht zu schneiden
- weniger Klappern
```

Alternative:

```text
Alu-U-Profil mit Filz/Teflonband gedämpft
```

Aber für Version 1 ist Kunststoff einfacher.

---

# Türtasche

Die Türtasche ist der rechte Bereich, in den die Tür hineinfährt.

## Anforderungen

```text
- frei von Futterbereich, Liegefläche und Kabeln halten
- Zugriff für Wartung ermöglichen
- ausreichend breit für Türplatte + etwas Spiel
- Schiene durchgehend bis in die Türtasche führen
- Tür darf im offenen Zustand den Eingang komplett freigeben
```

## Standardbox

```text
Türtasche: ca. 38 cm
Türplatte: ca. 32 cm breit
Reserve:   ca. 6 cm
```

## Largebox

```text
Türtasche: ca. 45 cm
Türplatte: ca. 37 cm breit
Reserve:   ca. 8 cm
```

---

# Schnurschleife – Grundprinzip

Die Tür wird durch eine geschlossene Schnurschleife bewegt.

```text
Draufsicht / Prinzip

        M Motorrolle                          U Umlenkrolle
          ○======================================○
          ║                                      ║
          ║                                      ║
          ○======================================○
                    │
                    │ Befestigungspunkt an Tür D
                    ▼
                   [D]
```

Motor dreht Richtung A:

```text
Tür öffnet nach rechts.
```

Motor dreht Richtung B:

```text
Tür schließt nach links.
```

---

# Warum geschlossene Schnurschleife?

Besser als Gummiband, weil:

```text
- Motor kontrolliert Öffnen und Schließen.
- Kein ausleierndes Gummiband.
- Keine unkontrollierte Rückstellkraft.
- Türbewegung besser vorhersehbar.
```

---

# Schnurmaterial

Geeignet:

```text
- geflochtene Nylon-Schnur
- Polyester-Schnur
- Dyneema-Schnur
- dünne, nicht elastische Angelschnur
```

Nicht geeignet:

```text
- Baumwollschnur
- Wollfaden
- stark elastische Schnur
```

Empfehlung:

```text
Durchmesser ca. 1–2 mm
nicht elastisch
reißfest
glatt
```

---

# Motorposition

## Empfehlung

Motor rechts oben in der Türtasche oder im angrenzenden Technikfach.

```text
Front innen / Draufsicht vereinfacht

┌────────────────────────────────────────────┐
│ E Eingang        T Türtasche               │
│                 ┌──────────────┐           │
│                 │ M Motor      │           │
│                 └──────────────┘           │
└────────────────────────────────────────────┘
```

Vorteile:

```text
- Motor ist weg vom Futterbereich.
- Kabelwege ins Technikfach sind kurz.
- Motor ist zugänglich.
- Katze kommt nicht direkt an den Motor.
```

---

# Umlenkrolle

Auf der Gegenseite der Schnurschleife wird eine Umlenkrolle benötigt.

Geeignet:

```text
- kleine Kunststoffrolle
- kleine Rolle mit Kugellager
- Mini-Seilrolle
```

Nicht ideal:

```text
- Schnur nur über Schraube oder Holzöse laufen lassen
```

Grund:

```text
Das wäre lauter und verschleißt die Schnur schneller.
```

---

# Befestigung der Schnur an der Tür

An der Tür braucht es einen kleinen Befestigungspunkt.

Möglichkeiten:

```text
- kleine Öse
- kleiner Winkel
- kleine Schraube mit Unterlegscheibe
- kleines Kunststoffteil als Klemmstück
```

Wichtig:

```text
- Befestigung darf nicht in der Schiene schleifen.
- Befestigung muss stabil sein.
- Schnur muss nachspannbar bleiben.
```

Empfehlung:

```text
Befestigung oben oder seitlich an der Tür, nicht unten im Schmutzbereich.
```

---

# Endschalter

Es werden zwei Endschalter verwendet.

```text
S1 = Tür geschlossen
S2 = Tür offen
```

## Geschlossen-Endschalter S1

Position:

```text
am linken Endpunkt, wenn Tür den Eingang vollständig verdeckt
```

Funktion:

```text
Tür ist zu → S1 gedrückt → Motor stoppt → Zustand LOCKED
```

## Offen-Endschalter S2

Position:

```text
rechts in der Türtasche, wenn Tür den Eingang vollständig freigibt
```

Funktion:

```text
Tür ist offen → S2 gedrückt → Motor stoppt → Zustand OPEN
```

---

# Endschalter nicht als harte Anschläge nutzen

Die Endschalter sollen nur erkennen, nicht die ganze mechanische Kraft aufnehmen.

Deshalb zusätzlich:

```text
- weicher Anschlag geschlossen
- weicher Anschlag offen
```

Material:

```text
- Moosgummi
- Filz
- Silikonpuffer
- Gummipuffer
```

Ziel:

```text
kein lautes Klack
kein Motor gegen Holz
Endschalter wird nur leicht und zuverlässig gedrückt
```

---

# Weiche Schließkante

An die schließende Kante der Tür kommt ein weiches Profil.

Möglichkeiten:

```text
- Moosgummi-Streifen
- Silikonprofil
- Filzleiste
```

Zweck:

```text
- Geräusch reduzieren
- Verletzungsrisiko senken
- weicher Kontakt, falls etwas im Weg ist
```

Wichtig:

Die Software und Lichtschranken müssen trotzdem verhindern, dass die Tür auf eine Katze schließt. Die weiche Kante ist nur eine zusätzliche Sicherheitsstufe.

---

# Bewegungsgeschwindigkeit

Zielwerte:

```text
Öffnen:    ca. 2–4 Sekunden
Schließen: ca. 2–4 Sekunden
```

Nicht schneller.

Warum:

```text
- leiser
- sicherer
- Katze erschrickt weniger
- Sensoren haben genug Reaktionszeit
```

Die Geschwindigkeit wird später per PWM im Code eingestellt.

---

# Manuelle Notbewegung

Die Tür sollte im stromlosen Zustand per Hand bewegbar bleiben.

Anforderung:

```text
- kein komplett selbsthemmender Mechanismus
- Tür darf nicht dauerhaft mechanisch blockieren
- im Notfall von außen zugänglich/verschiebbar
```

Optional:

```text
- kleine Serviceöffnung
- abnehmbare Abdeckung der Türtasche
- manuelle Zugmöglichkeit an der Tür
```

Ziel:

```text
Eine Katze darf nicht durch Elektronikfehler dauerhaft eingesperrt werden.
```

---

# Wartungszugang

Die Türmechanik muss erreichbar bleiben.

Zugänglich halten:

```text
- Motorrolle
- Umlenkrolle
- Schnurspannung
- Endschalter
- Schienen
- Sensoren im Türbereich
```

Zugang über:

```text
- oberen Klappdeckel
oder
- abnehmbare Abdeckung der Türtasche
```

---

# Mechanischer Test ohne Elektronik

Vor Motor/ESP32-Test muss die Mechanik per Hand funktionieren.

Checkliste:

```text
[ ] Tür läuft per Hand leicht.
[ ] Tür verkantet nicht.
[ ] Tür fällt nicht aus der Schiene.
[ ] Tür verdeckt Eingang vollständig.
[ ] Tür gibt Eingang vollständig frei.
[ ] Türtasche ist groß genug.
[ ] Schienen sind parallel.
[ ] Keine Schraube blockiert die Laufbahn.
[ ] Endschalter werden sauber berührt.
[ ] Weiche Anschläge funktionieren.
[ ] Schließkante ist weich.
```

---

# Mechanischer Test mit Motor, aber ohne Katze

```text
[ ] Motor öffnet in korrekter Richtung.
[ ] Motor schließt in korrekter Richtung.
[ ] Tür fährt gleichmäßig.
[ ] Schnur rutscht nicht.
[ ] Schnur springt nicht ab.
[ ] Offen-Endschalter stoppt Bewegung.
[ ] Geschlossen-Endschalter stoppt Bewegung.
[ ] Anschläge sind leise.
[ ] Tür kann bei Strom aus manuell bewegt werden.
```

---

# Anforderungen an den Holzbau

Für den Freund / Mechanik-Part:

```text
- Türplatte gerade zuschneiden.
- U-Schienen exakt parallel setzen.
- Türtasche frei und zugänglich lassen.
- Motorhalterung stabil, aber entkoppelt bauen.
- Motor möglichst mit Gummi/Moosgummi gegen Vibration lagern.
- Umlenkrolle gerade ausrichten.
- Schnur nachspannbar machen.
- Endschalter justierbar montieren.
- Weiche Anschläge einplanen.
```

---

# Anforderungen an Elektronik/Software

Für den Code später:

```text
- Motor nie ohne Timeout laufen lassen.
- Endschalter offen stoppt Öffnen.
- Endschalter geschlossen stoppt Schließen.
- Lichtschranke blockiert Schließen.
- Blockade beim Schließen: stoppen und wieder öffnen.
- PWM langsam genug einstellen.
- Fehlerzustand: Motor aus.
```

---

# Offene Punkte vor finalem Bau

Diese Punkte hängen von echten Bauteilen ab:

```text
- exakter U-Schienenquerschnitt
- exakte Türplattenstärke
- exakter Motor-Typ
- Durchmesser der Motorrolle
- Umlenkrollenmodell
- genaue Schnurlänge
- Endschaltermodell
- Motorhalterungsmaße
- ob Schnur reicht oder Zahnriemen besser wird
```

---

# Ergebnis Zeichnungspaket 04

Gesetzt ist:

```text
Box A:
- Türplatte ca. 32 x 36 cm
- 3–4 mm Sperrholz
- Schienenlänge ca. 70 cm
- Türtasche ca. 38 cm

Box B:
- Türplatte ca. 37 x 42 cm
- 4–5 mm Sperrholz
- Schienenlänge ca. 85 cm
- Türtasche ca. 45 cm

Gemeinsam:
- Tür läuft innen hinter der Front
- Tür öffnet nach rechts
- obere und untere Kunststoff-U-Schiene
- 12V Getriebemotor ca. 30 RPM
- geschlossene Schnurschleife
- Umlenkrolle
- 2 Endschalter
- weiche Anschläge
- weiche Schließkante
- manuelle Notbewegung einplanen
```

---

# Nächstes Zeichnungspaket

Zeichnungspaket 05 sollte Technikfach + Elektronikposition beschreiben:

```text
- Position Technikfach
- Montageplatte
- Kabeldurchführungen
- Netzteil/Step-Down/ESP32/Motortreiber
- Zugentlastung
- Trennung Katzenraum/Elektronik
```
