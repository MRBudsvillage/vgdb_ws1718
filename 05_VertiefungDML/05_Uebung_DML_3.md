# Übung

Für folgende Aufgaben werden die Tabellen Vertreter, Verkauf und Artikel verwendet.

## Aufgabe 1
Wie viel kostet der teuerste Artikel?

### Lösung
```sql
SELECT MAX(apreis) MAX
FROM artikel;

```

## Aufgabe 2
Wie hoch ist die durchschnittliche Provision aller Vertreter?

### Lösung
```sql

SELECT AVG(PROVISION)	MeanProv
FROM Vertreter;


```

## Aufgabe 3
Wie viele Artikel hat der Vertreter Mueller insgesamt verkauft?

### Lösung
```sql

SELECT SUM(anzahl) 
FROM verkauf		
WHERE VNR = (SELECT VNR FROM VERTRETER WHERE VNAME = 'Mueller');

```

## Aufgabe 4
Wie viele Wintermäntel hat der Vertreter Jahred insgesamt verkauft?

### Lösung
```sql

SELECT SUM(anzahl) 
FROM verkauf		
WHERE VNR = (SELECT VNR FROM VERTRETER WHERE VNAME = 'Jahred')
AND ANR = (SELECT ANR FROM ARTIKEL WHERE ANAME = 'Wintermantel');


```

## Aufgabe 5
Wessen Provision liegt über der durchschnittlichen Provision aller Vertreter?
> Tipp: Nutze hier eine Unterabfrage, um den Durchschnitt aller Vertreter zu ermitteln.

### Lösung
```sql
SELECT vname 
FROM vertreter
WHERE provision > (Select AVG(Provision) FROM Vertreter);
```

