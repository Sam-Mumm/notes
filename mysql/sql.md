# SQL

## Suchen
```
SELECT <*>, <spalte1>, <spalte2>, <spalte3>, ...
FROM <tabelle1>, <tabelle2>, <tabelle1>, ...
WHERE <Bedingung>
```

## Einfügen
```
INSERT INTO <tabelle> (<spalte1>, <spalte2>, <spalte3>, ...)
VALUES (<wert1>, <wert2>, <wert3>, ...)
```

## Ändern
```
UPDATE <tabelle>
SET <spalte1>=<value1>, <spalte2>=<value2>, <spalte3>=<value3>, ...
WHERE <Bedingung>
```

## Löschen
```
DELETE FROM <tabelle>
WHERE <Bedingung>
```

## Anlegen von einer Datenbank
```
CREATE DATABASE <datenbankname> CHARACTER SET <Zeichensatz>
```

## Anlegen von einer Tabelle 
```
CREATE TABLE <tabelle> (
	<spalte1> <datentyp> <eigenschaft>
)
```
gültige Datentypen u.a.
  * INT
  * VARCHAR(N)
  * TIMESTAMP

gültige Eigenschaften u.a.
  * NOT NULL
  * PRIMARY KEY
  * AUTO_INCREMENT
  * UNSIGNED