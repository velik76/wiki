# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Normen in der Medizintechnik](#normen-in-der-medizintechnik)
  - [IEC 82304](#iec-82304)
  - [EN 62304](#en-62304)
  - [Lastenheft vs Pflichtenheft](#lastenheft-vs-pflichtenheft)
  - [Verifizierung](#verifizierung)
  - [Validierung](#validierung)
  - [Klinische Bewertung](#klinische-bewertung)
  - [Softwareanforderungen](#softwareanforderungen)
  - [EN 62366](#en-62366)

## Normen in der Medizintechnik

In der Medizintechnik steht Sicherheit an erster Stelle, geht es doch um die Gesundheit und oft sogar um das Überleben von Patienten. Daher ist die Entwicklung von Produkten in der Medizintechnik stark reglementiert und durch Normen und Regeln abgesichert. Neben der Norm 60601, die die Sicherheitsanforderungen und ergonomischen Anforderungen an medizinische elektrische Geräte und in medizinischen Systemen regelt, gibt es 4 weitere wichtige Normen:

- EN 62304: Medizingeräte-Software-Lebenszyklus-Prozess
- ISO 14971: Anwendung des Risikomanagements auf Medizinprodukte
- ISO 13485: Anwendung des Qualitätsmanagements auf Medizinprodukte
- EN 62366: Anwendung der Gebrauchstauglichkeit auf Medizinprodukte
- IEC 82304-1: Health Software - General Requirements for product safety
- EN 60601-1-6: Usability
- EN 60601-1-8: Alarmnorm
- EN 60601-1 Allgemeine Festlegungen
- EN 60601-1-1 System-Norm (nur anwendbar mit EN 60601-1:1990, Inhalt wurde mittlerweile in Abschnitt 16 der EN 60601-1:2006 integriert)
- EN 60601-1-2 EMV-Norm
- EN 60601-1-3 Allgemeiner Strahlenschutz, Diagnostik
- EN 60601-1-4 Software-Norm (nur anwendbar mit EN 60601-1:1990, Inhalt wurde mittlerweile in Abschnitt 14 der EN 60601-1:2006 integriert)
- EN 60601-1-6 Gebrauchstauglichkeit
- EN 60601-1-8 Alarmsysteme
- EN 60601-1-9 Reduzierung von Umweltauswirkungen
- EN 60601-1-10 Physiologisch geschlossene Regelkreise
- EN 60601-1-11 Medizintechnik in häuslicher Umgebung
- EN 60601-1-12 Medizintechnik in der Umgebung für den Notfalleinsatz (Norm-Entwurf)

## IEC 82304

"The purpose of the standard is to establish product requirements for standalone software, i.e. software products not running on a dedicated hardware. IEC 82304-1 could be seen as an equivalent to IEC 60601-1 with the difference that the later includes a dedicated hardware for the software to run on. (And of course have a lot of hardware requirements!)"

<http://aligned.ch/blog/53-tips-tricks/232-5-quick-questions-on-iec-82304>

## EN 62304

**SCHADEN** physische Verletzung oder Schädigung der Gesundheit von Menschen oder Schädigung von Gütern oder der Umwelt

**RISIKO** Kombination der Wahrscheinlichkeit des Auftretens eines SCHADENS und des Schweregrades dieses SCHADENS

**GEFÄHRDUNG** potentielle Quelle eines SCHADENS

**RISIKOANALYSE** systematische Auswertung verfügbarer Informationen, um GEFÄHRDUNGEN zu identifizieren und RISIKEN abzuschätzen

Artikel zu Software-Lebenszyklus-Prozessen und der IEC 62304 liegt hier [Link](https://www.johner-institut.de/beratung/wissen-und-werkzeuge/artikel/artikel-zur-iec-62304/)

- Klasse A: Keine Verletzung oder Schädigung der Gesundheit ist möglich. 
- Klasse B: Keine schwere Verletzung ist möglich.
- Klasse C: Tod oder schwere Verletzung ist möglich.

Die Norm IEC 62304 fordert für eine Software der Klasse A nur die Software-Anforderungen und die Software-Freigabe

## Lastenheft vs Pflichtenheft

Ein Lastenheft beschreibt aus Auftraggeber-Sicht das Entwicklungsprojekt. Häufig beinhalten Lastenhefte eine krude Mischung verschiedenster Aspekte wie:

- Nutzungsanforderungen
- Marktanforderungen
- Gesetzliche Anforderungen
- System-Anforderungen
- Technische und organisatorische Rahmenbedingungen
- Markt-/Umsatzerwartungen
- Vorgaben für Prozesse, Methoden und Werkzeuge.

Ein Pflichtenheft beschreibt auf Auftragnehmersicht das zu entwickelnde Produkt bzw. das umzusetzende Projekt. Ebenso wie viele Lastenhefte umfassen Pflichtenhefte verschiedenste Aspekte und trennen nicht sauber zwischen

- Stakeholder-Anforderungen
- System-Anforderungen
- System-Architektur
- Prozessvorgaben
- Organisatorische und technische Rahmenbedingungen

Sowohl eine ISO 13485 also auch die FDA im 21 CFR part 820 unterscheiden zwischen Stakeholder-Anforderungen und Design Input:

- Stakeholder-Anforderungen umfassen die Nutzungsanforderungen, die gesetzlichen Anforderungen, Marktanforderungen sowie die fachlichen und organisatorischen Anforderungen.
- Der Design Input kann beispielsweise als Systemspezifikation (z.B. in Form eines UI-Prototyps) vorliegen.

<https://www.johner-institut.de/blog/iec-62304-medizinische-software/lastenheft-pflichtenheft-systemspezifikation/>

## Verifizierung

Verifizierung ist ein Prüfen der Systemanforderungen

## Validierung

Validierung ist ein Prüfen der Nutzungsanforderungen

Unter Validierung versteht man eine Prüfung mit objektiven Mitteln, ob spezifizierte Nutzer im spezifizierten Nutzungskontext die spezifizierten Nutzungsziele erreichen.

## Klinische Bewertung

[Link](<https://www.johner-institut.de/blog/tag/klinische-bewertung/>
Zweckbestimmung)

Dieses Dokument stellt die Basis für die Entwicklung Ihres Medizinprodukts dar. Fehlt es, ist es falsch, unvollständig oder unverständlich, werden Sie wahrscheinlich im Lauf der Entwicklung nicht nur auf regulatorische Probleme stoßen. Üblicherweise lesen sich Auditoren und Inspektoren dieses Dokument auch zu allererst. Nehmen Sie sich die Zeit, es sorgfältig zu erstellen!
[Link](https://www.johner-institut.de/blog/regulatory-affairs/zweckbestimmung/)

## Softwareanforderungen

Daher sollte eine SRS beschreiben:

- Benutzerschnittstelle(n)
- Die GUI: Positionierung von Elementen, Style Guides, …
- Verhalten des Systems auf Benutzeraktionen im Normal- und Fehlerfall: Vom System angezeigte Informationen, Berechnungen, Grafiken, Meldungen, Warnungen, “Screenflow”, …
- Die Geschwindigkeit, mit der diese Reaktionen geschehen
- Auf welchen Umgebungen, sich die Software (Blackbox) installieren lassen soll (Betriebssystem, vorausgesetzte Datenbanken und andere Server, Hardware einschließlich RAM) und wie diese Installation von statten gehen soll.
- Wie sich das System auf Benutzerfehler und Überlast reagieren soll.
- Technische Schnittstellen (zu anderen Systemen)

<https://www.johner-institut.de/blog/tag/software-anforderungen/>

## EN 62366

Die IEC 62366 verlangt bei der Validierung der Gebrauchstauglichkeit repräsentative Anwender. Wie viele das sind, sagt sie aber nicht. Das geht auch kaum, schließlich hängt die Anzahl auch davon ab, wie homogen die verschiedenen Nutzergruppen sind.

<https://www.johner-institut.de/blog/iec-62366-usability/usability-validierung/>
