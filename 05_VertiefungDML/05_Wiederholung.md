# Übungen

Im folgenden Skript werden die Beispiel-Tabellen `VERTRETER`, `VERKAUF` und `ARTIKEL` verwendet.

## Aufgabe 1
Führe das SQL-Skript [DB-Vertreter](./SQL_-_DB-Vertreter.sql) in SQLPlus aus, um die Tabellen anzulegen und mit Beispieldaten zu füllen. Wie lautet dein Befehl um das SQL-Skript auszuführen?

### Lösung
```sql
start SQL_-_DB-Vertreter.sql

```

## Aufgabe 2
Mache dich mit den Tabellen vertraut bzgl.:
* Spalten und Datentypen
* Beziehung der Tabellen zueinander
* Datensätzen in den Tabellen und was diese bedeuten

## Aufgabe 3
Zeige alle Vertreter mit `NAME` und `VNR` an, die eine Provision von  weniger als 7% erhalten. 

### Lösung
```
SELECT NAME, VNR
FROM VERTRETER
WHERE PROVISION < 0.07;
```

## Aufgabe 4
Bei welchen Artikeln (`NAME` und `ARTIKELNUMMER`) liegt der Preis über `100`?

### Lösung
```sql
SELECT NAME, ANR
FROM ARTIKEL
WHERE APREIS > 100;
```

## Aufgabe 5
Zeige alle Vertreter an, die vor dem 01.10.1980 geboren sind und deren Namen ein i beinhaltet

```sql
SELECT *
FROM VERTRETER 
WHERE to_date(GEBURTSDATUM, 'DD.MM.YYYY') < '01-DEC-1980'
AND vname LIKE '%i%'; 
````

## Aufgabe 6

Füge dich selbst als Vertreter in die Tabelle hinzu

```sql
INSERT INTO VERTRETER
values (7777, 'Nico Wolf', '23-DEC-1995', 0.07);
```
## Aufgabe 7
```sql
INSERT INTO VERKAUF
values (1014, 7777, 13, 22, sysdate);
```

## Aufgabe 8

```sql
UPDATE ARTIKEL
SET APREIS = 88.90
WHERE ANAME = 'STIEFEL';

``` 

## Aufgabe 9

```sql

ALTER TABLE VERTRETER 
ADD (bonus NUMBER(4,0));

```	

## Aufgabe 10

```sql

UPDATE VERTRETER
SET bonus = 500;

```
## Aufgabe 11
```sql
ALTER TABLE VERTRETER
MODIFY (VNAME VARCHAR(20));
```

## Aufgabe 12
```sql
SELECT DISTINCT DATUM
FROM VERKAUF; 
``` 