# Übungen

Führe das Skript [DB-Vertreter](./SQL_-_DB-Vertreter.sql) aus.

## Aufgabe 1
Lege für die Tabellen `VERTRETER`, `VERKAUF` und `ARTIKEL` Primary Key Constraints (`PK`) an.

### Lösung
```sql
ALTER TABLE vertreter
ADD	CONSTRAINT PKVERT PRIMARY KEY(VNR);

ALTER TABLE verkauf
ADD CONSTRAINT PKVERK PRIMARY KEY(unr);

ALTER TABLE artikel
ADD CONSTRAINT PKART PRIMARY KEY(anr);

```

## Aufgabe 2
Lege für die Tabelle `VERKAUF` alle notwendigen Foreign Key Constraints (`FK`) an.

### Lösung
```sql
CREATE TABLE verkauf
(
	FK NUMBER(4,0),
	CONSTRAINT FK FOREIGN KEY(anr) REFERENCES verkauf(artikel)
);

```

## Aufgabe 3
Lösche den Foreign Key Constraint `FK_DEPTNO`. Dieser ist für die Spalte `DEPTNO` in der Tabelle `EMP` definiert.

### Lösung
```sql
ALTER TABLE EMP
DROP CONSTRAINT FK_DEPTNO;


```

## Aufgabe 4
Lege den benötigten Foreign Key Constraint (`FK`) für die Tabelle `EMP` neu an.

### Lösung
```sql
ALTER TABLE emp
ADD CONSTRAINT fk_deptno FOREIGN KEY(deptno) REFERENCES dept;

```

