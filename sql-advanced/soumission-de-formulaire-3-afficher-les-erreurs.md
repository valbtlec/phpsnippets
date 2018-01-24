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

* création d'un système d'affichage de message de succes, info, etc

 * creation de la fonction dans function.php
 * creation du partial - _flash.php


```php
<?php if(isset($_SESSION['notification']['message'])): ?>
	<div class="alert alert-"<?= $_SESSION['notification']['type'] ?> ">
		<h4><?= $_SESSION['notification']['message'] ?></h4>
	</div>
<!-- on vide la notification -->
<?php $_SESSION['notification']=[];?>
<?php endif; ?>
```





