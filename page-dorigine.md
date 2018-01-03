 * page a l'origine de la demande - exemple page avec un formulaire :
 
   * form.php :

```php

<form action="traitement.php">
```
traitement.php

```php
$_SERVER['HTTP_REFERER'];       => renvoi l'adresse de form.php
	    
```



* page à l'orgine de la demande sans query string



```php
$referer=$_SERVER['HTTP_REFERER'];
// retirer la query string
$referer = reset((explode('?', $referer)));

```

