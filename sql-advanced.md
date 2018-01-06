#SQL ADVANCED

https://youtu.be/es_t9QXpXY4

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


```sql
SELECT a.nom, a.nom
FROM btlec a, btlec b where a.nom=b.nom
```



plus rapide en calcul :
```sql
SELECT a.nom, b.nom
FROM btlec a
JOIN btlec b ON 
a.nom=b.nom
```



jointure sur 2 vraies tables :

la liste des noms par services :



```sql
SELECT btlec.nom, services.full_name 
FROM services 
JOIN btlec
ON btlec.id_service = services.id
order by 
services.full_name 
```



astuce renommer arbitrairement les tables en l pour left et r pour right afin de mieux trouver le type de jointure adaptée



```sql
SELECT r.nom, l.full_name 
FROM services l 
JOIN btlec r
ON r.id_service = l.id
order by 
l.full_name
```



si je veux toute la liste des noms btlec qu'ils soient ou non assignés à un service :



```sql
SELECT r.nom, l.full_name 
FROM services l 
RIGHT JOIN btlec r
ON r.id_service = l.id
order by 
l.full_name
```




#agregation

le nombre de compte btlec


```sql
select count(*) AS "nb user btlec" from btlec;
```




la quantité total de produits commandés pour une facture



```sql
select 'total", orderNumber, sum(quantityOrdered) from orderdetails where ordernumber= 10100;
```



la quantité total de produits commandés pour chaque facture



```sql
select 'total", orderNumber, sum(quantityOrdered) from orderdetails 
group by orderNumber;
```




#sous requetes

on veut la moyenne d'article commandé :


```sql
select avg(quantityOrdered) from orderdetails;
```
 ensuite, on veut tout les lignes de produits commandés pour les quelle la quantité de produit est supérieure à cette moyenne
 
 


```sql
 select orderNum, productCode, quantityOrdered from orderDetails where quantityOrdered >
 (
  select avg(quantityOrdered) from orderdetails;
 )
order by ordernumber;

```

Avec in (sous requete renvoi plusieurs résultats)

```sql
SELECT *  
FROM 
msg table_msg 
LEFT JOIN 
replies table_replies 
ON table_msg.id = table_replies.id_msg 
WHERE table_replies.id_msg= :idMsg 
AND 
date_reply 
IN (SELECT max(date_reply) FROM replies GROUP BY id_msg
```





#more

https://youtu.be/FKSSOpQe5Jc
http://csharp-video-tutorials.blogspot.fr/p/free-sql-server-video-tutorials-for.html

Fonction d'agrégation :

SELECT msg, sum(rep) FROM msg => erreur
SELECT msg, sum(rep) FROM msg GROUP BY msg => ok

Filtrer : where ou having
filtre avant agrégation
SELECT msg, sum(rep) FROM msg WHERE msg='blue' GROUP BY msg 
filtre après
SELECT msg, sum(rep) FROM msg  GROUP BY msg HAVING msg='blue'
