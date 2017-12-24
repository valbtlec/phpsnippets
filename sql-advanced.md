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

orders deviendra o et customer c gace au from : **c.customername, o.orderdate**


```sql
SELECT o.orderid AS "Numero de facture", c.customername, o.orderdate FROM customers c, orders o where c.customerid=o.customerid;

SELECT b.nom, b.prenom, s.id, s.full_name AS "nom service" FROM btlec b, services c where b.id_service=s.id



```

##jointure naturelle


renvoie 2 colonnes identiques avec la totalité de user id
a et b sont considérées par mysql comme 2 tables différentes


SELECT a.`id_user`, b.`id_user` from
stats_logs a, stats_logs b where a.`id_user` =b.`id_user`

afficher les users id qui existent dans les 2 tables donc tous !!

SELECT a.`id_user`, b.`id_user` from
stats_logs a
JOIN
stats_logs b 
ON a.`id_user` =b.`id_user`








