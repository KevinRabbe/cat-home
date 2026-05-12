# Sicherheitsanforderungen

Dieses Dokument sammelt feste Sicherheitsregeln für die RFID-Katzen-Futterboxen.

Status: verbindliche Projektanforderung für die private Prototyp-Version.

---

# Grundsatz

Die Katze darf im Innenraum der Box nichts erreichen können, was zur Türsteuerung, Elektronik oder Mechanik gehört.

Der Katzenraum muss aus Sicht der Katze glatt, passiv und sicher sein.

---

# Keine erreichbare Mechanik im Katzenraum

Im Katzenraum darf nicht erreichbar oder sichtbar sein:

```text
- Schnüre
- Drähte
- Kabel
- Motor
- Umlenkrollen
- Endschalter
- offene U-Schienen
- offene Schiebetürmechanik
- Elektronikmodule
- Schraubklemmen
- Steckverbinder
- lose Abdeckungen
```

Begründung:

```text
Katzen würden daran spielen, ziehen oder kratzen.
Dadurch könnte die Türsteuerung kaputtgehen oder unsicher werden.
```

---

# Konsequenz für die Türmechanik

Die Schiebetürmechanik muss vollständig eingehaust werden.

Empfohlene Front-Konstruktion:

```text
Außenfront
↓
verdeckter Tür-/Mechanikkanal
↓
Innenblende / Schutzverkleidung
↓
Katzenraum
```

Die Katze sieht innen nur:

```text
- glatte Innenwand
- abgerundeten Eingang
- eventuell bündig verbaute Sensoröffnungen
```

Die Katze darf nicht sehen oder erreichen:

```text
- Schnurschleife
- Motorrolle
- Umlenkrolle
- Endschalter
- Kabel
- Motorkabel
- Schienenmechanik
```

---

# Geschlossener Tür-/Mechanikkanal

Die Tür und ihr Antrieb laufen in einem geschlossenen Bereich.

Dieser Bereich muss:

```text
- für Katzen unzugänglich sein
- für Menschen wartbar sein
- von außen oder über Serviceklappe erreichbar sein
- keine offenen Spalten in den Katzenraum haben
- stabil genug gegen Pfoten/Kratzen sein
```

Wartung darf nur möglich sein über:

```text
- oberen Klappdeckel
- abnehmbare Serviceabdeckung
- äußeres Technikfach
```

Nicht über offenliegende Teile im Katzenraum.

---

# Kabelschutz

Alle Kabel müssen geschützt geführt werden.

Regeln:

```text
- keine losen Kabel im Katzenraum
- keine Kabel entlang Liegefläche oder Futterbereich
- Kabel direkt durch Bohrungen ins Technikfach führen
- Kabeldurchführungen entgraten oder mit Gummitülle schützen
- Kabel gegen Zug sichern
- Sensorleitungen möglichst kurz und geschützt führen
```

---

# Sensoren im Katzenraum

Sensoren dürfen nur bündig oder geschützt montiert werden.

Erlaubt:

```text
- kleine bündige Sensoröffnung
- versenkte Lichtschranke im Rahmen
- Sensor hinter Schutzblende
```

Nicht erlaubt:

```text
- herausstehende Platinen
- sichtbare Kabel
- frei erreichbare Sensorhalter aus dünnem Draht
- lose verklebte Sensoren im Innenraum
```

---

# Futter- und Liegebereich

Der Futter- und Liegebereich bleibt mechanikfrei.

Dort darf nur sein:

```text
- Futterpodest
- herausnehmbarer Einsatz
- Kerbl-Näpfe
- Matte/Kissen
- glatte Innenwände
```

Nicht dort platzieren:

```text
- Technikfach
- Motor
- Schnurführung
- Netzteil
- offene Kabelkanäle
```

---

# Servicezugang

Weil die Mechanik verdeckt ist, braucht sie einen sauberen Servicezugang.

Einplanen:

```text
- abnehmbare Abdeckung für Türtasche/Mechanikkanal
oder
- Zugang über oberen Klappdeckel
oder
- Zugang über seitliches Technikfach
```

Servicezugang muss ermöglichen:

```text
- Schnur nachspannen
- Schnur wechseln
- Motor prüfen
- Umlenkrolle prüfen
- Endschalter justieren
- Schienen reinigen
```

---

# Manuelle Notbewegung

Auch bei verdeckter Mechanik muss die Tür im Notfall manuell bewegbar oder entriegelbar bleiben.

Anforderung:

```text
- keine dauerhaft blockierende Mechanik
- kein kompletter Einschluss bei Stromausfall
- manuelle Öffnung von außen oder über Servicezugang möglich
```

---

# Finaler Sicherheitsgrundsatz

```text
Alles, was sich bewegt, Strom führt oder zur Türsteuerung gehört, muss hinter eine Abdeckung.
Alles, was die Katze erreichen kann, muss glatt, abgerundet, stabil und passiv sein.
```

Diese Regel ist verbindlich für die weitere Konstruktion.
