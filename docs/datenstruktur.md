# Datenstruktur

## Person
```js
role: Role[]
id: String

```
Weitere Informationen kommen vorraussichtlich aus Identity-Management der TH-Köln.
## Resource
Bspw: Raum 3.204, Mobiles Whiteboard, Sitzplatz im PC-Pool, Schließfach 

```js
id: String
name: String
description: String
responsible: Person[]
image: Image[]
bookingConditions: Condition[]
```

### Condition
Bspw. muss bestimmte Role haben, eine woche zuvor buchen, buchung bestätigen, first come first serve, windhund
```js
name: String
```

#### SubConditions (Has Role, BookingPeriod, ApprovalBy, etc.) extends Condition

### Room extends Resource 

```js
etage: String
roomnumber: String
building: Building
width: Float
length: Float
height: Float
windowOrientation: Enum('North', 'NorthWest', etc.)[]
staticEquipment: staticEquipment[]
mobileEquipment: mobileEquipment[]
360image: 360image[]

```
#### Building
```js
name: String
address: String
rooms: Room[]
```

### Equipment extends Resource
> Keine Consumables!
```js
id: String
type: Enum('Tafel', 'WhiteBoard', 'Beamer', etc.)
location: Room
mobility: Enum('static', 'mobile')
```

<!-- ### StaticEquipment extends Equipment 
Bspw: Tafel, Stühle, Beamer

Fest zugeorndet, nicht entfernbar.

```js

```

### mobileEquipment extends Equipment 

```js

``` -->
### Sitzplatz extends Resource
Bspw. in PC-Pool, Labor?!

```js
location: String
room: Room
equipment: Equipment[]
```
Equipment hier zum Beispiel Ausstattung/Specs der PC's.

<!-- 
### Schließfach extends Resource
```js
location: String
room: Room
equipment: Equipment[]
``` -->
## Booking
```js
bookedBy: Person
participants: Person[]
timeslots: Timeslot[]
title: String
type: Enum('Vorlesung', 'Studentische Arbeitsgruppe', 'Übung', etc.)
conditionsMett: ConditionsMett[]
```

### Timeslot
```js
start: DateTime
end: DateTime
```

### ConditionsMet
```js
condition: Condition
approved: Boolean
approvelDate: DateTime
approvedBy: Person?
```
