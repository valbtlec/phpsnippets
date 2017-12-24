#SQL ADVANCED

## jointure simple

```sql

SELECT * FROM customers, orders where customers.customerid=orders.customerid;

```


renommer des colonnes
```sql
SELECT orders.orderid AS "Numero de facture" FROM customers, orders where customers.customerid=orders.customerid;

```



