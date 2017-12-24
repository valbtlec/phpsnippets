#SQL ADVANCED

## jointure simple

jointure simple

```sql

SELECT btlec.nom, btlec.prenom, services.id, services.full_name FROM `btlec`, services where btlec.id_service=services.id;

```


jointure simple + renommage des colonnes
```sql

SELECT btlec.nom, btlec.prenom, services.id, services.full_name AS "nom service" FROM `btlec`, services where btlec.id_service=services.id

SELECT orders.orderid AS "Numero de facture" FROM customers, orders where customers.customerid=orders.customerid;

```

jointure simple + renommage des tables

btlec deviendra b et services s grace au FROM : **btlec b, services c**


```sql
SELECT b.nom, b.prenom, s.id, s.full_name AS "nom service" FROM btlec b, services s where b.id_service=s.id
```

##jointure naturelle


renvoie 2 colonnes identiques avec la totalité de user id
a et b sont considérées par mysql comme 2 tables différentes



SELECT a.nom, a.nom
FROM btlec a, btlec b where a.nom=b.nom

plus rapide en calcul :
SELECT a.nom, b.nom
FROM btlec a
JOIN btlec b ON 
a.nom=b.nom


jointure sur 2 vraies tables :

la liste des noms par services :

SELECT btlec.nom, services.full_name 
FROM services 
JOIN btlec
ON btlec.id_service = services.id
order by 
services.full_name 









