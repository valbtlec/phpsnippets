#formatage date sql pour affichage

Il existe plusieurs solutions 

 * au niveau php
 
//strtotime
date('d-m-Y', strtotime($value['date_msg']));

//datetime
$date=new DateTime($value['date_msg']);
$date=$date->format('d-m-Y');

 * au niveau sql 
  