

```php
function cleanData($data)
{

	//supprime les antislashes
	$data=stripslashes($data);
	
	//converti les saut de ligne en saut de ligne
	$data=nl2br($data);
	//converti les caractères spéciaux en entités html
	$data=htmlspecialchars($data);

	//supprime les balises html et php d'une chaine
	$data=strip_tags($data);
	
	return $data;
}
```

