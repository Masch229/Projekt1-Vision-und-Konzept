# Condition Service

_Der Condition Service implementiert Abfragen, ob eine bestimmte Aktion einer Identität erlaubt oder unerlaubt ist. Ist die Bedingung eine Freigabe durch eine Person, wird diese digital beantragt._

Ressourcen Besitzer können Ihren Ressourcen Bedingungen (mit Parametern) zuordnen.

Um erfolgreich eine Buchung abzuschließen, müssen alle (der Ressource zugeordneten) Bedingungen erfüllt sein.

## Conditions

Bedingungen werden in zwei Kategorien eingeteilt:

1. _Pre-Conditions_ - können bereits vor einer Buchungs-Anfrage geprüft werden. Beispielsweise: Person hat ausreichende Berechtigungen. Ressource ist für den Zeitraum nicht gebucht.
2. _Post-Conditions_ - werden während oder nach einer Buchung-Anfrage geprüft bzw. verändert. Beispielsweise: Freigabe durch Ressourcen Besitzer.

Bedingungen können einen Status haben:

- `met`: alle Bedingungen sind erfüllt. Oder Ressource hat keine Bedingung verknüpft.
- `notmet`: eine oder alle Bedingungen sind nicht erfüllt. Buchungs-Anfrage dementsprechend abgelehnt.
- `pending`: Ressource benötigt z.B. Freigabe durch Owner und ist daher nicht `met`.

Bedingungen haben **keine** Hierarchie.

### Pre-Conditions (Auszug)

- `isRessourceAvailable`
- `isAllowedToBook`
- `isOnTime`: Buchungs-Anfrage muss beispielsweise 2 Tage vorher erfolgen
- `maxDuration`

### Post-Conditions (Auszug)

- `hasEnoughtContigent`: ein Studierender kann beispielsweise nur einen Raum gleichzeitig gleichzeitig Buchen.
- `isApprovedByOwner`
