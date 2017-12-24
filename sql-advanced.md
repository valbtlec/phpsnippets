#SQL ADVANCED

## jointure simple

jointure simple

```sql

SELECT * FROM customers, orders where customers.customerid=orders.customerid;

```


jointure simple + renommage des colonnes
```sql
SELECT orders.orderid AS "Numero de facture" FROM customers, orders where customers.customerid=orders.customerid;

```

jointure simple + renommage des tables

orders deviendra o et customer c gace au from : **c.customername, o.orderdate**


```sql
SELECT o.orderid AS "Numero de facture", c.customername, o.orderdate FROM customers c, orders o where c.customerid=o.customerid;

```

##jointure naturelle


renvoie 2 colonnes identiques avec la totalité de user id
a et b sont considérées par mysql comme 2 tables différentes


SELECT a.`id_user`, b.`id_user` from
stats_logs a, stats_logs b where a.`id_user` =b.`id_user`



SELECT a.`id_user`, b.`id_user` from
stats_logs a
JOIN
stats_logs b 
ON a.`id_user` =b.`id_user`






