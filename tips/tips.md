#astuces
 
 * encodage - string - accents - utf8
Il faut forcer l'encodage de l'objet lorsque l'on envoi un mail en php, sinon les accents et autre sont transformé en hiéroglyphes

(utilisé dans la page contact du portail bt)

```php
$objMag="PORTAIL BTLec - demande envoyée";
mb_internal_encoding('UTF-8');
$objMag = mb_encode_mimeheader($objMag);
```



 * personnaliser le title quand on utilise des partials pour le header
 
 dans le fichier _header :
 

```html
<title>
 <?php
 isset($title) ? $title : 'titre par défaut';
?>
 </title>
```

