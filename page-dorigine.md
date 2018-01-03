

```php
/*page a l'origgine de la demande
	exemple page avec un formulaire :
	    form.php :
	        <form action="traitement.php">
	    traitement.php
	        $_SERVER['HTTP_REFERER'];       => renvoi l'adresse de form.php
	    
	*/
	$referer=$_SERVER['HTTP_REFERER'];
	// retirer la query string
	$referer = reset((explode('?', $referer)));
```

