# Sichtschutz

**Kontoauszüge für Behördenanträge rechtssicher schwärzen – lokal im Browser, ohne Upload.**

Wer Grundsicherung, Wohngeld, BAföG, Kinderzuschlag oder Prozesskostenhilfe beantragt, muss Kontoauszüge vorlegen. Darin stehen Apotheke, Kirche, Gewerkschaft, Therapie, Vereine – Daten, die das Amt nichts angehen. Das Bundessozialgericht hat 2008 entschieden (Az. B 14 AS 45/07 R): Bei **Ausgaben** darf der Empfänger geschwärzt werden, wenn besonders geschützte Daten betroffen sind; **Beträge, Kontostände und Einnahmen bleiben sichtbar**.

Sichtschutz setzt genau diese Regel um:

- Die PDF wird **nur im Browser** verarbeitet. Nichts verlässt das Gerät, kein Konto, kein Server.
- Buchungen und sensible Kategorien werden über ein **offenes Regelwerk** erkannt (Muster, keine KI).
- Es werden **nur erlaubte Schwärzungen** vorgeschlagen; jede lässt sich per Tipp korrigieren.
- Der Text wird **wirklich entfernt** – die betroffenen Bereiche werden als Bild neu aufgebaut, kein Balken, den man wegklicken kann.
- Ein **Schwärzungsprotokoll** wird angehängt: Datum und Betrag jeder teilweise geschwärzten Buchung, Rechtsgrundlage, SHA-256 des Originals. Die sensible Kategorie wird bewusst nicht genannt.

## Ausprobieren

Prototyp online: **https://lilith568.github.io/sichtschutz/**

Beim Start wird ein erfundener Muster-Kontoauszug geladen. Eigene PDF per Drag & Drop oder Dateiauswahl laden – auch die bleibt lokal.

Lokal: `index.html` im Browser öffnen. Es wird eine Internetverbindung zu cdnjs.cloudflare.com (pdf.js, pdf-lib) und Google Fonts benötigt; die eigentliche Verarbeitung läuft offline.

## Stand (Oktober 2026)

Klickbarer Prototyp, eine Datei:

- PDF laden, Textläufe zu Zeilen und Buchungen rekonstruieren, Richtung (Soll/Haben) erkennen
- Kategorien per Regelwerk, strenger Modus (nur BSG-Urteil) und erweiterter Modus
- Schwärzung prüfen und korrigieren, geschwärzte PDF mit Protokoll exportieren

Noch offen (geplant für die Förderphase):

- Scans und Fotos (lokale OCR mit tesseract.js)
- Robuste Erkennung für mindestens acht Bankformate mit gemessener Genauigkeit
- Kern als eigenständige Bibliothek `redact-core` (npm, CLI) und validiertes Regelwerk-Format
- Leckage-Tests (Annotationen, Metadaten, inkrementelle Updates, unsichtbarer Text)
- Barrierefreiheit nach WCAG 2.2 AA, Nutzertests mit Beratungsstellen

## Technik

TypeScript/JavaScript ohne Server-Komponente. pdf.js für Text und Layout, pdf-lib für den Neuaufbau, Web Crypto für Hashes. Regelwerk als JSON (Kategorie, Muster, Rechtsgrundlage, Sprache).

## Mitmachen

Issues und Pull Requests sind willkommen – besonders echte Bankformate (bitte **nur synthetische oder vollständig anonymisierte** Auszüge, niemals echte Daten) und Hinweise aus der Sozialberatung, welche Schwärzungen Behörden akzeptieren.

## Lizenz

[Apache-2.0](LICENSE)

## Hinweis

Sichtschutz ist keine Rechtsberatung. Behörden legen die Regeln unterschiedlich aus; im Zweifel vorher nachfragen oder eine Beratungsstelle einbeziehen.
