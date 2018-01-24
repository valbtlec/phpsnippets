* creation du partial d'affichage d'erreur :

```php
if(isset($errors)&& count($errors)!=0){

	echo '<div class="danger">';

	foreach ($errors as $error) {
		echo $error .'<br>';
	}

	echo '</div>';
}
```

on l'inclue ensuite au bon endroit au niveau de la view


