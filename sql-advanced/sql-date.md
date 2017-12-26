## GESTION DES DATES AVEC MYSQL


la date actuelle


```sql

NOW()  //renvoi une date sous forme : YYYY-MM-JJ HH:MM:SS
```

découper une date dans une requete :



```sql
SELECT DAY(date) AS jour, MONTH(date) AS mois, YEAR(date) AS annee, HOUR(date) AS heure, MINUTE(date) AS minute, SECOND(date) AS seconde FROM table
```

formater une date




```sql
SELECT DATE_FORMAT(date, '%d/%m/%Y %Hh%imin%ss') AS date FROM table //renvoie DD/MM/YYYY HHhMMSS49s ( 11/03/2010 15h47min49)
```

