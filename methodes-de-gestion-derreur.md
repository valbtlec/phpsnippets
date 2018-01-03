
## creation d'une fonction perso d'affichage des erreurs



```php
//notre fonction d'affichag edes erreurs
function customError($errno, $errstrg){
    echo "<br>Error : $errno : $errstrg </br>";
    die();
}

// on définie notre foncyion en callback du set_error_handler() 
set_error_handler("customError");
    
//On va ici ignorer le rapport d'erreurs standard de PHP, et utiliser notre fonction perso
// il sera possible de déclencher une erreur grâce à trigger_error()

```

#affiner notre fonction - 1

```php
//pour mémoire on peut préciser tout ces arguments + le contexte
function my_error_handler($no, $str, $file, $line){
     echo '<p>Erreur ['.$no.'] : '.$str.'<br/>';
     echo 'Survenue dans le fichier : "'.$file.'" à la ligne '.$line.'.</p>';
 }

```


#affiner notre fonction - 2


```php
// gestion avancé d'erreur : en fonction de l'erreur renvoyée, on affiche un message différent
function my_error_handler($no, $str, $file, $line){
    switch($no){
        // Erreur fatale
        case E_USER_ERROR:
            echo '<p><strong>Erreur fatale</strong> : '.$str.'</p>';
            exit;//on arrete le script
            break;
        
        // Avertissement
        case E_USER_WARNING:
            echo '<p><strong>Avertissement</strong> : '.$str.'</p>';
            break;
        
        // Note
        case E_USER_NOTICE:
            echo '<p><strong>Note</strong> : '.$str.'</p>';
            break;
        
        // Erreur générée par PHP
        default:
            echo '<p><strong>Erreur inconnue</strong> ['.$no.'] : '.$str.'<br/>';
            echo 'Dans le fichier : "'.$file.'", à la ligne '.$line.'.</p>';
            break;
    }
}
```

##compléments d'infos :

trigger_error() nécessite 2 arguments :

le message d'erreur
le type d'erreur (optionnel, par défaut E_USER_NOTICE).



```php
if(empty($_GET['empty'])){
    trigger_error('Vous devez préciser la valeur de "empty" ou une valeur nulle lui sera imposée.', E_USER_NOTICE);
    $empty = 0;
}
 
if(empty($_GET['div']))
    trigger_error('Vous ne pouvez pas diviser par 0', E_USER_WARNING);
else
    echo (5/$_GET['div']);
 
if(!is_file('non-existing'))
    trigger_error('Un fichier indispensable à l\'exécution du script est manquant.', E_USER_ERROR);
```



//restore_error_handler() permet de réutiliser l'ancienne version de gestion des erreurs (qui peut être la fonction PHP par défaut, ou une autre fonction utilisateur) ;7

//error_get_last() (PHP >= 5.2.0) renvoie un array contenant les informations à propos de la dernière erreur survenue



