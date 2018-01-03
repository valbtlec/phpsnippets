 * page a l'origine de la demande


```php
//exemple page avec un formulaire :
//form.php :
<form action="traitement.php">

//traitement.php
$_SERVER['HTTP_REFERER'];       => renvoi l'adresse de form.php
	    
```



* page à l'orgine de la demande sans query string

$referer=$_SERVER['HTTP_REFERER'];
// retirer la query string
$referer = reset((explode('?', $referer)));
