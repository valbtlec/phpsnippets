#les formulaires : la base


* recupérer toutes les valeurs $_POST

```php
extract($_POST);

```



* conserver les valeur saisies si formulaire soumis mais non complet :

```html

<input placeholder="Objet" name="objet" id="objet" type="text" value="<?=isset($objet)? $objet: false?>">
```


* éviter le renvoi renvoi du formulaire après traitement


```php
unset($objet,$msg,$name,$email);

```

 * sécuriser le php self

```php
<!-- sécuriser le php self -->
<form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]);?>">
```

