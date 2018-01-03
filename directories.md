$_SERVER["DOCUMENT_ROOT"]
dirname(__FILE__)
DIRECTORY_SEPARATOR 
PATH_SEPARATOR
set_include_path()
get_include_path()
$_SERVER['PHP_SELF']


#chemins absolus


```php
//To use absolute paths, use the following code where the first slash indicates starting from the domain name:
$INC_DIR = $_SERVER["DOCUMENT_ROOT"]. "/inc/"; 
include($INC_DIR. "common.php"); 
$_SERVER['HTTP_HOST']
```

#inclure des fichiers correctement :


```php
//to include or require a file, we use this
require dirname(__FILE__) . DIRECTORY_SEPARATOR . 'my_file.php';

//...include a file relative to file path:
include(dirname(__FILE__) . '/path/relative/file_to_include.php');
```

#modifier la valeur de l'include_path

```php
//set_include_path — Modifie la valeur de la directive de configuration include_path
// permet de tj avoir la racine du site
set_include_path( get_include_path() . PATH_SEPARATOR . $_SERVER['DOCUMENT_ROOT'] ); 
set_include_path(get_include_path() . PATH_SEPARATOR . $path);
```

#exemples de retour des fonctions, variables serveurs


```php
// depuis le fichier C:\inetpub\wwwroot\btlec_dev\portail\_config\config.php
dirname(__FILE__)
// retourne : C:\inetpub\wwwroot\btlec_dev\portail\_config\

$_SERVER['PHP_SELF']
//renvoi :btlec_dev/portail/_config/config.php

dirname($_SERVER['PHP_SELF']);
//renvoi :   /btlec_dev/portail/_config

echo $_SERVER['HTTP_HOST'] 
//renvoi : 172.30.92.53

echo "http://".$_SERVER['HTTP_HOST'].dirname($_SERVER['PHP_SELF']);
//output:  http://s3lab.com/Shaz3e-ResponsiveFramework/S3-CMS/_source



```

