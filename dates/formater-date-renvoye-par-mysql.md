#formatage date sql pour affichage

Il existe plusieurs solutions 

 * au niveau php
 
//strtotime
date('d-m-Y', strtotime($value['date_msg']));

//datetime
$date=new DateTime($value['date_msg']);
$date=$date->format('d-m-Y');

 * au niveau sql 
 
 ```sql
SELECT DATE_FORMAT(date, '%d/%m/%Y %Hh%imin%ss') AS date FROM table //renvoie DD/MM/YYYY HHhMMSS49s ( 11/03/2010 15h47min49)
```