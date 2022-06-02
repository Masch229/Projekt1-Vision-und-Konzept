# Interview Stundenplanteam

Dieses Interview bestand aus zwei Teilen, zum einen wurden uns Informationen zu möglichen Projekten in einem Treffen in Präsenz gegeben, zum anderen wurden weitere Fragen in einer Mail beantwortet

## Allgemeine Projektideen

Anwesend: Studenplanteam (Alex Dobrynin, Uwe Müsse, Dennis Dubbert), Christopher, Benedikt, Tim, Yannic, Marius
Protokollant: Benedikt

**Datum: 04.05.2022 - 12:00 Uhr**

_Main-Outcome: 3 Projekte vorhanden, welche als P1 an uns outgesourcet werden können_

### Stundenplan

- Ziemlich viele Anforderungen und komplexe Datenstruktur
- Hier könnten aber selber nochmal neue Anforderungen gesammelt werden
- Hybrid/Präsenz | Blockveranstaltungen | Überschneidungen etc. sind wichtige Themen
- UI-Focus wäre cool, weil darauf grade nicht der Schwerpunkt liegt
- HOPS kann nur Anzeige, neues System soll auch Planung können, sodass Professor\*innen auch eintragen können (von zentral zu dezentral)

### Raumbuchungssystem

- Sehr wenig Gedanken bisher da / am wenigsten erforscht ⇒ Chance am höchsten das es wirklich genutzt wird
- Hängt auch mit dem Stundenplan & Prüfungen zusammen (auch semesterübergreifend)
- Möglichkeit mit transponder verwaltung zu koppeln
- Sollte Buchungen annehmen können (von Stundenplan, Studierenden, Dozenten usw.)
  - Developer API wäre gut (bzw. teil der API sein)
- Verschiedene Berechtigungen (Kontingente, Prio auf bestimmte Räume, etc.)
- Ausstattung (Technisch, plätze, art der plätze) sollte auch drin sein
- Tages- und Stundengenau planbar sollte es sein
- Eigenständiger Service
- Was wird zur Authentifizierung genutzt? GM-Id, mit dummydaten? keyclog?
- Wie sind Ressourcen und Saten strukturiert?
- Wegführung vielleicht noch mit rein?
- QR-Codes an Räumen welche dir die Infos bietet & Buchung ermöglicht
- Genehmigungen für Räume (bspw. Labore)
- Welche Räume gehören zum Campus? Was kommt mit rein?
- Räume gehören Instituten, wären sehr viele Ansprechpartner; nur anhand erstmal an einer Etage
- Stakeholder: Lehrende, Studierende, Institute (raumhoheit und Rechtemanagment), Hausmeister (für Wartungen), Pförtner, Dekanatsasistent,
- Kapazität der Plätze müsste flexibel gehlaten sein (PANDEMIE)
- Raumtypen, etc bräuchte auch die Stundnenplanplanung
- Modularität, systemarchitektur, eventuell mehrere Microservices

=> Viel Freiraum, nur schnittstelle wichtig

### Git Modulhandbuch (sehr Technisch)

- Eigener Modulhandbuchservice welcher aus Git-Repos zieht
- Bisher überall verteilt und veraltet
- Als Quelle der Wahrheit für die Studenplanung (hierfür Hooks)
- Übertragen von Handbüchern aus extern into Git
- Was für stadien haben die Modulhandbücher?
- Wer darf daten bearbeiten? Abnahmen von Studiengangsleitern etc. müssen erfolgen ⇒ ablauf ähnlich wie bei Pull-Requests
- Wie kann Git als datenmanagment genutzt werden mit externer Maske
- Prozess bisher über Git sehr technisch
- Daten sollten bei Eingabe validiert werden (CP nur ints, etc.); weniger Prosa mehr Möglichkeiten um dinge anzugene Prüfungsform angegben)
- Prüfungsamt möchte eine PDF mit allen Modulen und daten pro studiengang
- Historie ist sehr wichtig um Modulbeschreibung von alten Modulen einzusehen
- Konsistenz schaffen
- Schema von Modulen kann uns gegeben werden/ was ist wenn prüfungsordnung sich ändert
- Verbindung von Pflichtmodulen aus einem Studiengang als Wahlmodul im anderen / was ist mit daten (CP-Anzahl; Prüfungsform) die anders sind
- Interviewpartner: Prüfungsamt, CN, Mario Winter, Stefan Bente (hat selber schonmal was angefangen auf Basis von GitLab)
- Was für eine Plattform nutzt man? Github, selfhosted plattform?
- Technologien sind komplett egal - Schnittstelle wichtiger

## Weitere Anforderungen aus Mail

### Anforderungen Raumplanung:

- Räume der TH abbilden
  - Raumausstattung (Sitzplätze, Tische, Materialien, Beamer etc.) -> Mobiliar beweglich?
  - Raumtypen
- Rollensystem (unterschiedliche Rechte)
  - Rollenauthentifizierung über Keycloak
  - Studentengruppen (auch mit Kontingenten)
  - Raumabhängig (z.B. Mitarbeiter für Räume in Fächern die sie betreuen)
  - Lehrende, Studierende, Administratoren, Mitarbeiter, Angestellte etc.
- Zeitkontingente für Studierende (auch studiengang- bzw. fachabhängig)
- Unterschiedliche Rechte
  - Z.B. Lehrende > Studierende (Können Buchungen überschreiben)
- Kalender bzw. Buchungssystem
- Auch als Schnittstelle nach außen verfügbar (z.B. für Stunden- und Prüfungsplanung)
- Buchungen für Prüfungsplanung
- Filtern nach Typ, Ausstattung, Zeit, Rechte etc.
- Verschiedene Buchungstypen für unterschiedliche Veranstaltungstypen
  - Z.B. Veranstaltung, Externe (Firmen etc.), Studentenbuchung etc.
  - Unterscheidung: Dauerbuchung vs. Einzelbuchung
- Semesterplan und Feiertage etc. berücksichtigen
  - Z.B. Blockwochen
- Benachrichtigungssystem
  - Hat Buchung geklappt?
  - Wurde Buchung überschrieben?
  - Ist Zeitkontingent verändert worden?
  - Etc.

### Nice to have

- Rauminformation per Schild-Scanner
- Wann gebucht (Kalenderansicht über das Semester)
- Art der Buchungen
- Was drin (aktuelle Belegung und Ausstattung)
- Rechte
- Etc.

### Mögliche Erweiterungen (geringere Prio als Nice to have)

- Navigationssystem durch die TH
