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





