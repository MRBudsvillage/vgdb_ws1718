# Übungen

Löse die Aufgaben durch `JOIN` der Tabellen.

## Aufgabe 1
Erzeuge eine Ausgabe, in der jeder Vertreter (`VNR` und `VNAME`) mit all seinen Verkäufen (`DATUM`, `ANZAHL` und `ANR`) gelistet wird.

### Lösung
```sql

SELECT VEERTRETER.VNR, VNAME
FROM VERTRETER
INNER JOIN VERKAUF ON VERTRETER.VNR = VERKAUF.VNR;

```

## Aufgabe 2
Reduziere die Ausgabe aus Aufgabe 1 auf Vertreter und ihre Verkäufe, bei denen mehr als 10 Artikel verkauft wurden.

### Lösung
```sql
SELECT VERTRETER.VNR, VNAME
FROM VERTRETER
INNER JOIN VERKAUF ON VERTRETER.VNR = VERKAUF.VNR
WHERE ANZAHL > 10;
```

## Aufgabe 3
Ergänze die Ausgabe aus Aufgabe 2 um den Namen und den Preis der jeweils verkaufen Artikel.
Verwende dazu zwei JOIN-Befehle wie unten dargestellt.


##Lösung 

```sql

SELECT VERTRETER.VNR, VNAME, ANAME, APREIS 
FROM VERTRETER
INNER JOIN VERKAUF ON VERTRETER.VNR = VERKAUF.VNR
 INNER JOIN ARTIKEL ON ARTIKEL.ANR = VERKAUF.ANR
 WHERE ANZAHL > 10;
```


## Aufgabe 4
Zeige für den Verkäufer mit `VNR` = `1010` alle Verkäufe (`ANZAHL`, `DATUM`) an, die sich auf Stiefel oder Wintermäntel beziehen und am `27.06.2015` getätigt wurden.

### Lösungen
```sql
SELECT ANZAHL, DATUM
FROM VERTRETER
INNER JOIN VERKAUF on VERTRETER.VNR = VERKAUF.VNR
WHERE DATUM = to_date('27-JUN-2015')
AND VERKAUF.VNR = 1010
AND VERKAUF.ANR IN(12,13);



```
