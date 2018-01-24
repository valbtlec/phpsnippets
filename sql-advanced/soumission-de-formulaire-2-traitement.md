 * envoi du mail d'activation :
 


```php
 if(count($errors==0))
{
	//envoi d'un mail d'activation
	$to=$email;
	$subject= WEBSITE_NAME . " - activation de compte";
	$token=sha1($pseudo.$email.$password);

	ob_start();
	require('templates/email/activation.tmpl.php');
	$content=ob_get_clean();

	//format html	
	$headers  = 'MIME-Version: 1.0' . "\r\n";
    	 	$headers .= 'Content-type: text/html; charset=iso-8859-1' . "\r\n";

	//envoi
 	mail($to,$subject,$content,$headers);

}
```

notre template :

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	
</head>
<body>
	<h1>activation de compte</h1>

	Pour activer votre compte, veuilllez cliquer sur le lien ci-dessous :
	<a href="<?= WEBSITE_URL .'/activation.php?p='.$pseudo. '&amp;token='.$token ?>">lien d'activation</a>

</body>
</html>
```


