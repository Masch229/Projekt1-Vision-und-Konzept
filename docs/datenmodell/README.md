![Meilenstein 5: Datenmodell bis zum 01.09.2022](../assets/progress-05.png)

<div style="display: flex; justify-content: space-between;">
  <a href="../architekturentwurf">Zurück</a>
  <a href="../projektabschluss">Weiter</a>
</div>

# Datenmodell

Manche der im Architekturentwurf vorgestellten Komponenten benötigen eine interne Datenhaltung. Es werden ERDs für die jeweiligen Services vorgestellt, die die grobe Datenstruktur beschreiben. Dabei muss die finale Datenhaltung nicht zwingend als relationale Datenbank implementiert sein. Es gibt auch andere Datenbankparadigmen, die diese Strukturen ähnlich abbilden können (z.B. Dokumentbasierte Datenbanken). Welches Paradigma für welche Komponente verwendet werden sollte, muss kurz vor beziehungsweise zur Implementationszeit entschieden werden.

## Condition Service

Der Condition Service verfügt über die komplexeste Datenhaltung der Komponenten. Es werden *Conditions* (Bedingungen) verwaltet, die von einem Bedingungstypen sind und über Eingabeparameter verfügen. Eine Bedinung muss einer Ressource zugeordnet werden. Wird aus dem Booking Service eine Buchung für eine Ressource angefragt, wird ein *Check* (Abfrage) im Condition Service erstellt. Diese Abfrage gibt die Parameterwerte an die jeweilen Bedingungen weiter und überprüft den Status. Weitere Informationen über die Conditions finden sie [hier](../ConditionService.md)
### Datenmodell

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
| 2 | "allowedRoles" | [Student, Prof] |
| 3 | "timeInAdvanceInHours" | 24 |
| 5 | "timeInAdvanceInHours" | 24 |

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

### Datenmodell

![Datenmodell Booking Service](../assets/datenmodell-booking-service.png)

### Beispieldaten

| bookingId | resourceId | bookedBy | from | to | status
|--|--|--|--|--|--|
| 1 | THK-GM01-0301  | ybruegge |  01.10.2022 12:00 |  01.10.2022 13:00 | booked  |
| 2 | THK-CGN01-0200 | bengel   |  04.10.2022 09:30 |  01.10.2022 10:30 | pending |

## Equipment Service

Dieser Service verwaltet Ressourcen und Equipment. Ressourcen sind grundsätzlich alles, was buchbar ist, wie Räume oder ein mobiles Whiteboard. Eine Ressource kann über Equipment verfügen, wie beispielsweise die Ausstattung eines Raumes. Equipment und Ressourcen können durch weitere dynamische Eigenschaften erweitert werden.

### Datenmodell

![Datenmodell Equipment Service](../assets/datenmodell-equipment-service.png)

### Beispieldaten

**Resource Types**

| name | 
|--|
| room |
| workplace |
| smartboard |

**Resources**

| resourceId | resourceType | name |
|--|--|--|
| 1 | room | "3216 - MI Studio" |
| 2 | smartboard | "Microsoft Smartboard" |
| 3 | workplace | "Workstation 01" |
| 4 | room | "3215 - 360° Vorlesungsraum" |

**Resource Properties**

| resourceId | name | value |
|--|--|--|
| 1 | "size" | "25m²" |
| 1 | "seats" | "50" |
| 1 | "seatingType" | "loose" |
| 2 | "size" | "40 inches" |
| 2 | "brand" | "Microsoft" |
| 2 | "model" | "Surface Hub Pro 3" |
| 3 | "software" | "Paint, Word, Gimp" |

**Equipment Types**

| name | 
|--|
| projector |
| 3Dcameras |
| smartboard |

**Eqipment**

| equipmentId | equipmentType | name | resourceId |
|--|--|--|--|
| 1 | projector | "Main Projector" | 1 |
| 2 | smartboard | "Philips Smartboard" | 1 |
| 3 | 360CameraSystem | "12 360° Camera System" | 4 |

**Equipment Properties**

| resourceId | name | value |
|--|--|--|
| 1 | "connectors" | "HDMI, DisplayPort" |
| 1 | "resolution" | "1920x1080" |
| 2 | "size" | "33 inches" |
| 2 | "brand" | "Philips" |
| 2 | "model" | "PX03" |
| 3 | "Working Cameras" | "8/12" |

## Location Service

Als Stammdatenservice verwaltet der Location Service Daten zu *Locations* (Standorte wie z.B. Campus) *Buildings* (Gebäuden) und *Rooms* (Räumen).

### Datenmodell
![Datenmodell Location Service](../assets/datenmodell-location-service.png)

### Beispieldaten

**Locations**

| locationId | name |
|--|--|
| 1 | "TH Köln - Campus Gummersbach" |
| 2 | "TH Köln - Campus Deutz" |
| 3 | "TH Köln - Campus Südstadt" |

**Buildings**

| buildingId | name | locationId |
|--|--|--|
| 1 | "Bibliothek" | 1 |
| 2 | "Kino" | 1 |
| 3 | "Geb. 3 (Mensagebäude)" | 1 |
| 4 | "Geb. 4 (Hörsaalgebäude)" | 1 |
| 5 | "Geb. 1 (Hauptgebäude)" | 1 |
| 6 | "Geb. 2 (Hauptgebäude)" | 1 |

**Rooms**

| roomId | name | buildingId |
|--|--|--|
| 1 | "Arbeistraum 1" | 1 |
| 2 | "3216 - MI Studio" | 6 |
| 3 | "Mensa" | 3 |
| 4 | "3215 - 360° Vorlesungsraum" | 6 |

<div style="display: flex; justify-content: space-between;">
  <a href="../architekturentwurf">Zurück</a>
  <a href="../projektabschluss">Weiter</a>
</div>
