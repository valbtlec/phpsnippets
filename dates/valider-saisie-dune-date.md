#valider format d'une date



```php
// vérifie qu'on est au format 2017-12-10   Y-m-d
if( preg_match ( "/([12]\d{3}-(0[1-9]|1[0-2])-(0[1-9]|[12]\d|3[01]))/" , $_POST['date'] ) )
```

