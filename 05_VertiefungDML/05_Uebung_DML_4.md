# Übung

## Aufgabe 1
Zeige alle Vertreter mit `NAME` und `VNR` an, deren Name länger als `6` Zeichen ist.

### Lösung
```sql

SELECT vname, vnr
FROM vertreter
WHERE LENGTH(vname) > 6;

```

## Aufgabe 2
Zeige alle Vertreter, die im Juli oder im Mai geboren sind.

### Lösung
```sql

SELECT vname
FROM vertreter
WHERE TO_CHAR(geburtsdatum, 'mm') = '05'
OR TO_CHAR(geburtsdatum, 'mm') = '07';
 

```

## Aufgabe 3

Erzeuge folgende Ausgabe:

| VNR  | VNAME_UP | PROV_GRD  |
| ---- | -------- | --------- |
| 1010 | MUELLER  | ,1        |
| 3401 | SCHMITZ  | ,1        |
| 5337 | RITSCH   | ,1        |
| 4321 | JAHRED   | 0         |

### Lösung
```sql


SELECT vnr, 	UPPER(vname) VNAME_UP,
			ROUND(provision,1) PROV_GRD
FROM vertreter;


```

## Aufgabe 4
Zeige alle Artikel an, die mit `Wi` beginnen. Löse diese Aufgabe mit der substr()-Funktion.

### Lösung
```sql

SELECT aname
FROM artikel
WHERE SUBSTR(aname,1,2) = 'Wi';



```

## Aufgabe 5
Erzeuge folgende Ausgabe:

| VNR   | VNAME   | DAT   |
| ----  | ------- | ----- |
| 1010  | Mueller | 03-05 |
| 3401  | Schmitz | 15-08 |
| 5337  | Ritsch  | 23-07 |
| 4321  | Jahred  | 27-12 |

### Lösung
```sql
SELECT vnr, 	vname,	
			TO_CHAR(geburtsdatum, 'dd-mm') DAT
FROM vertreter;
```

## Aufgabe 6
Zeige alle Vertreter (`VNR`, `VNAME`) an, die im selben Jahr geboren sind wie der Vertreter Jahred.

### Lösung
```sql
SELECT vnr, vname
FROM vertreter
WHERE TO_CHAR(Geburtsdatum, 'yyyy') = (
	SELECT TO_CHAR(Geburtsdatum, 'yyyy')
	FROM vertreter
	WHERE vname = 'Jahred');
	

```

## Aufgabe 7
Erhöhe bei den Vertretern den Bonus um `300`, die in einem Monat geboren sind, der `31` Tage hat.

### Lösung
```sql

UPDATE vertreter
SET bonus = bonus + 300
WHERE vnr IN (
SELECT vnr
FROM Vertreter
WHERE TO_CHAR(Geburtsdatum, 'mm') IN ( 
	SELECT TO_CHAR(LAST_DAY(Geburtsdatum), 'mm')
	FROM vertreter
	WHERE TO_CHAR(LAST_DAY(geburtsdatum), 'dd') = '31'
	)
);


```

