# Übung

Löse folgende Aufgaben mit Hilfe von Unterabfragen.

## Aufgabe 1
Zeige alle Vertreter (`VNR`, `VNAME`) an, die bereits Artikel mit der `ANR` = `13` verkauft haben.

### Lösung
```sql

SELECT Vertreter.VNR, VNAME
FROM VERTRETER
WHERE VERTRETER.VNR 
IN (Select VERTRETER.VNR from VERKAUF where ANR = 13);
```

## Aufgabe 2
Zeige alle Artikel (`ANR`, `ANAME`) an, die der Vertreter mit der `VNR` = `4321` am `27.06.2015` verkauft hat.

### Lösung
```sql
SELECT artikel.anr, aname
FROM artikel
WHERE artikel.anr 
IN (SELECT anr FROM verkauf WHERE vnr = 4321 AND DATUM = to_date('27-JUN-2015', 'dd.mm.yyyy'));

```

## Aufgabe 3
Zeige alle Vertreter (`VNR`, `VNAME`) an, die bereits Artikel verkauft haben, deren Preis über `100`€ liegt.

### Lösung
```sql

SELECT vertreter.vnr, vname
FROM vertreter
WHERE vertreter.vnr
IN (SELECT vnr FROM artikel WHERE artikel.apreis > 100);

```

## Aufgabe 4
Zeige alle Vertreter, die noch nie den Artikel mit der `ANR` = `22` verkauft haben.

### Lösung
```sql
SELECT vname
FROM VERTRETER
WHERE VNR 
NOT IN (Select VNR from VERKAUF WHERE ANR = 22);


```

## Aufgabe 5
Welche Vertreter (`VNR`) haben am `27.06.2015` mehr Artikel mit `ANR` = `12` verkauft als der Vertreter mit `VNR` = `4321`?

### Lösung
```sql
SELECT vnr 
FROM verkauf
WHERE anzahl >  (
	SELECT anzahl 
	FROM verkauf 
	WHERE DATUM = to_date('27.06.2015', 'dd.mm.yyyy') 
	AND vnr = (SELECT vnr FROM vertreter WHERE vname = 'Jahred')
	AND anr = (SELECT anr FROM artikel WHERE aname = 'Stiefel')
)
AND DATUM = to_date('27.06.2015', 'dd.mm.yyyy')
AND anr = (SELECT anr FROM artikel WHERE aname = 'Stiefel');




```

