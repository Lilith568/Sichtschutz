# Sichtschutz

**Redact bank statements for public authorities – legally sound, locally in your browser, no upload.**
*Deutsche Fassung weiter unten.*

Try it: download `index.html` and open it in your browser. Interface in English and German.

## The problem

People applying for basic income, housing benefit, student aid, child supplement or legal aid in Germany must hand over bank statements. Those statements reveal pharmacies, churches, trade unions, therapists, associations – data the agency has no business seeing. The German Federal Social Court ruled in 2008 (B 14 AS 45/07 R): for **expenses**, the payee may be redacted when special categories of personal data are involved; **amounts, balances and all income stay visible**. In practice people either don't redact at all, redact wrongly (amount gone, application bounced), or upload the most sensitive document they own to a third-party service that merely paints a box over text that is still in the file.

## What Sichtschutz does

- Processes the PDF **only in the browser**. Nothing leaves the device, no account, no server.
- Detects transactions and sensitive categories through an **open rule pack** (patterns, no AI).
- Proposes **only permitted redactions**; every one can be toggled with a tap.
- **Really removes** the text – affected regions are rebuilt as images, not covered with a bar that can be clicked away.
- Attaches a **redaction record**: date and amount of every partially redacted transaction, legal basis, SHA-256 of the original. The sensitive category is deliberately never named. The record is written in German because the German authority has to read it.

## Status (October 2026)

Clickable single-file prototype:

- Load PDF, rebuild lines and transactions from positioned text runs, detect direction (debit/credit)
- Categories via rule pack, strict mode (court ruling only) and extended mode
- Review and correct redactions, export redacted PDF with record
- UI in German and English

Planned for the funded phase:

- Scans and photos (local OCR with tesseract.js)
- Robust detection for at least eight bank layouts with measured precision/recall
- Core as a standalone library `redact-core` (npm, CLI) and a validated rule-pack format
- Leakage tests (annotations, metadata, incremental updates, invisible text)
- Accessibility to WCAG 2.2 AA, user tests with counselling centres

## Technology

TypeScript/JavaScript, no server component. pdf.js for text and layout, pdf-lib for rebuilding, Web Crypto for hashes. Rule pack as JSON (category, patterns, legal basis, locale). Open `index.html` locally; it needs cdnjs.cloudflare.com (pdf.js, pdf-lib) and Google Fonts at load time, the processing itself runs offline.

## Contributing

Issues and pull requests welcome – especially real bank layouts (**synthetic or fully anonymised statements only, never real data**), rule packs for other countries' welfare systems, and feedback from social counselling on what agencies accept.

## Transparency

The prototype was built with the help of generative AI (Claude, Anthropic) and is maintained and understood by a human. This is disclosed in funding applications.

## License

[Apache-2.0](LICENSE)

Not legal advice. Agencies interpret the rules differently; if in doubt ask a counselling centre first.

---

# Deutsch

**Kontoauszüge für Behördenanträge rechtssicher schwärzen – lokal im Browser, ohne Upload.**

Ausprobieren: `index.html` herunterladen und im Browser öffnen. Oberfläche auf Deutsch und Englisch.

## Das Problem

Wer Grundsicherung, Wohngeld, BAföG, Kinderzuschlag oder Prozesskostenhilfe beantragt, muss Kontoauszüge vorlegen. Darin stehen Apotheke, Kirche, Gewerkschaft, Therapie, Vereine – Daten, die das Amt nichts angehen. Das Bundessozialgericht hat 2008 entschieden (Az. B 14 AS 45/07 R): Bei **Ausgaben** darf der Empfänger geschwärzt werden, wenn besonders geschützte Daten betroffen sind; **Beträge, Kontostände und Einnahmen bleiben sichtbar**. In der Praxis schwärzen Menschen gar nicht, falsch (Betrag weg, Antrag kommt zurück) oder mit Online-Diensten, die den Auszug auf fremde Server laden und oft nur einen Balken drüberlegen, den man wieder entfernen kann.

## Was Sichtschutz macht

- Die PDF wird **nur im Browser** verarbeitet. Nichts verlässt das Gerät, kein Konto, kein Server.
- Buchungen und sensible Kategorien werden über ein **offenes Regelwerk** erkannt (Muster, keine KI).
- Es werden **nur erlaubte Schwärzungen** vorgeschlagen; jede lässt sich per Tipp korrigieren.
- Der Text wird **wirklich entfernt** – die betroffenen Bereiche werden als Bild neu aufgebaut, kein Balken, den man wegklicken kann.
- Ein **Schwärzungsprotokoll** wird angehängt: Datum und Betrag jeder teilweise geschwärzten Buchung, Rechtsgrundlage, SHA-256 des Originals. Die sensible Kategorie wird bewusst nicht genannt.

## Stand (Oktober 2026)

Klickbarer Prototyp in einer Datei: PDF laden, Buchungen und Richtung erkennen, Kategorien per Regelwerk, strenger und erweiterter Modus, Schwärzung prüfen und korrigieren, geschwärzte PDF mit Protokoll exportieren. Beim Start wird ein erfundener Muster-Kontoauszug geladen; alle Personen, Konten und Buchungen darin sind ausgedacht.

Geplant für die Förderphase: Scans per lokaler OCR, mindestens acht Bankformate mit gemessener Genauigkeit, Kern als Bibliothek `redact-core`, Leckage-Tests, Barrierefreiheit (WCAG 2.2 AA), Nutzertests mit Beratungsstellen.

## Mitmachen

Issues und Pull Requests sind willkommen – besonders echte Bankformate (bitte **nur synthetische oder vollständig anonymisierte** Auszüge, niemals echte Daten) und Hinweise aus der Sozialberatung, welche Schwärzungen Behörden akzeptieren.

## Transparenz

Der Prototyp ist mit Hilfe von generativer KI (Claude, Anthropic) entstanden und wird von einem Menschen gepflegt und verstanden. In Förderanträgen wird das offengelegt.

## Lizenz

[Apache-2.0](LICENSE)

Keine Rechtsberatung. Behörden legen die Regeln unterschiedlich aus; im Zweifel vorher eine Beratungsstelle fragen.
