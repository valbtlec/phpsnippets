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



