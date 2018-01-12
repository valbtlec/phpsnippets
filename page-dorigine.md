 * page précédente : récupérer l'adresse de la page 'précédente' 

```php
$_SERVER['HTTP_REFERER'];       => renvoi l'adresse de form.php
	    
```

* idem mais en retirant la query string


```php
$referer=$_SERVER['HTTP_REFERER'];
// retirer la query string
$referer = reset((explode('?', $referer)));

```


 * redirection sur la même page quand query string



```php
echo $_SERVER['PHP_SELF'] . '?' . $_SERVER['QUERY_STRING'];
```

mieux (xss)


```php
$url = $_SERVER['PHP_SELF'] . '?' . $_SERVER['QUERY_STRING'];
echo htmlspecialchars($url, ENT_QUOTES, 'utf-8');
```

