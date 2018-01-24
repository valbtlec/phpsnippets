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


```php
 if(!function_exists('set_flash'))
{
	function set_flash($message,$type='info')
	{
		$_SESSION['notification']['message']=$message;
		$_SESSION['notification']['type']=$type;

	}

}
```



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
 *  on inclue le partial dans le _header après l'inclusion de la nav
 
 * on utilise notre système dans les pages avec ou sans redirection (attention si on redirge, la page sur laquelle on redirige doit avoir un session_start)
 
 ex dans la page register, après l'envoi du mail :
 


```php
 set_flash("mail d'activation rnvoye", "succes");
 //option
 header('Location:index.php');
 exit();
```


 
 a noter si on ne met pas exit(), le message ne s'affiche pas
 




