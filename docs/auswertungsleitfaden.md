#Auswertungsleitfaden für die Stakeholder Interviews 

Im folgenden Dokument wird ein Leitfaden bereitgestellt mit dessen Hilfe das Maximum an Informationen aus den geführten Stakeholder Interviews extrahiert werden soll. Zusätzlich soll der Leitfaden einen Standard schaffen um unabhängig von den Bearbeitenden einheitliche Ergebnisse erzielt werden könne.


## Formulieren von Anforderungen

Die erhaltenen Antworten werden betrachtet und aus diesen sollen formale Anforderungen formuliert werden.

Dabei sollte folgende Satzschablone verwendet werden:




Diese wird wie Folgt verwendet:

1. Bestimmung der Wichtigkeit einer Anforderung
	- Muss: muss im aktuellen realease delivered werden
	- Sollte: ist optional
	- Wird: muss in einem zukünftigen release delivered werden
2. Art und und Typ der beschriebenen Funktion festlegen
	- Interface Anforderung: ein externes System ist involviert
	- Nutzer Interaktion: Das System bietet dem Nutzer eine Möglichkeit zur Interaktion
	- Unabhängige Systemaktivität
3. Welches Objekt gehört zur beschriebenen Funktion?
4. Logische und / oder temporäre Konditionen formulieren 
	- "Nach"/"Sobald": Definiert Zeitpunkte in denen das System Aktivitäten ausführt
	- "Während": Definiert Zeitfenster
	- "Im Falle / Wenn": Definiert eine logische Kondition


### Beispiel:

Frage:
Welche Informationen benötigen Sie, um einen passenden Raum zu finden? & Was würde Sie bei der Suche nach einem Raum unterstützen?
Antwort:
-   Ausstattung, Verfügbarkeit, Größe, Bestuhlung, Materialkoffer vor Ort?
-   Wichtig: wie gut funktioniert ein Raum für Workshops (hat er durch kontext wissen).
-   Problem sind auch sehr enge Räume wo nicht viel verschoben werden kann.
-   Raum Layout wäre daher super.

Formale Anforderung mit Satztemplate:

Wann/Unter welcher Voraussetzung | muss, soll, wird | das System | dem Nutzer/dem Admin/etc.(Objekt) anzeigen/verarbeiten/etc. | optional: zusätzliche Informationen über das Objekt

Wenn ein Nutzer auf einen verfügbaren Raum klickt | muss | das System | dem Nutzer eine Übersicht über (die Attribute Verfügbarkeit, Ausstattung, Größe, Bestuhlung, Materialkoffer) anzeigen | um den Entscheidungsprozess des Nutzers zu unterstützen
