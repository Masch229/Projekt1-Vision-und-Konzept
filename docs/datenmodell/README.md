![Meilenstein 5: Datenmodell bis zum 01.09.2022](../assets/progress-05.png)

<div style="display: flex; justify-content: space-between;">
  <a href="../architekturentwurf">Zurück</a>
  <a href="../projektabschluss">Weiter</a>
</div>


# Datenmodell

Manche der im Architekturentwurf vorgestellten Komponenten benötigen eine interne Datenhaltung. Es werden ERDs für die jeweiligen Services vorgestellt, die die grobe Datenstruktur beschreiben. Dabei muss die finale Datenhaltung nicht zwingend als relationale Datenbank implementiert sein. Es gibt auch andere Datenbankparadigmen, die diese Strukturen ähnlich abbilden können (z.B. Dokumentbasierte Datenbanken). Welches Paradigma für welche Komponente verwendet werden sollte, muss kurz vor beziehungsweise zur Implementationszeit entschieden werden.

## Condition Service

Der Condition Service verfügt über die komplexeste Datenhaltung der Komponenten. Es werden *Conditions* (Bedingungen) verwaltet, die von einem Bedingungstypen sind und über Eingabeparameter verfügen. Eine Bedinung muss einer Ressource zugeordnet werden. Wird aus dem Booking Service eine Buchung für eine Ressource angefragt, wird ein *Check* (Abfrage) im Condition Service erstellt. Diese Abfrage gibt die Parameterwerte an die jeweilen Bedingungen weiter und überprüft den Status. Weitere Informationen über die Conditions finden sie [hier](../ConditionService.md)
### ERD

![Datenmodell Condition Service](../assets/datenmodell-conditions-service.png)

### Beispieldaten

**Condition Types (ENUM)**

| name | 
|--|
| isRessourceAvailable |
| isAllowedToBook |
| isOnTime |
| maxDuration |
| hasEnoughtContigent |
| isApprovedByOwner |

**Parameter**

| condition | name | value | 
|--|--|--|
| 2 | allowedRoles | [Student, Prof] |
| 3 | timeInAdvanceInHours | 24 |
| 5 | timeInAdvanceInHours | 24 |

**Conditions**

| id | resourceId | conditionTypeId |
|--|--|--|
| 1 | THK-GM01-0301 | isRessourceAvailable |
| 2 | THK-GM01-0301 | isAllowedToBook |
| 3 | THK-GM01-0301 | isOnTime |
| 4 | THK-CGN01-0200 | isRessourceAvailable |
| 5 | THK-CGN01-0200 | isOnTime |

**Checks**

| bookingId | conditionId | status
|--|--|--|
| 1 | 1 | met |
| 1 | 2 | met |
| 1 | 3 | met |
| 2 | 4 | met |
| 2 | 5 | pending |



## Booking Service

Der Booking Service verwaltet ausschließlich Buchungen von Ressourcen. Alle weiteren Informationen werden aus den anderen Services abgefragt und Referenzen auf Datensätzen aus anderen Services abgespeichert.

![Datenmodell Booking Service](../assets/datenmodell-booking-service.png)

## Equipment Service

Dieser Service verwaltet Ressourcen und Equipment. Ressourcen sind grundsätzlich alles, was buchbar ist, wie Räume oder ein mobiles Whiteboard. Eine Ressource kann über Equipment verfügen, wie beispielsweise die Ausstattung eines Raumes. Equipment und Ressourcen können durch weitere dynamische Eigenschaften erweitert werden.

![Datenmodell Equipment Service](../assets/datenmodell-equipment-service.png)

## Location Service

Als Stammdatenservice verwaltet der Location Service Daten zu *Locations* (Standorte wie z.B. Campus) *Buildings* (Gebäuden) und *Rooms* (Räumen).

![Datenmodell Location Service](../assets/datenmodell-location-service.png)

<div style="display: flex; justify-content: space-between;">
  <a href="../architekturentwurf">Zurück</a>
  <a href="../projektabschluss">Weiter</a>
</div>
