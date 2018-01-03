##passer plusieurs valeurs en paramètre d'une requete préparée


```php
/* Exécute une commande préparée en utilisant un tableau de valeurs pour les clauses IN */
$params = array(1, 21, 63, 171);
/* Crée une chaîne pour les marqueurs */
$place_holders = implode(',', array_fill(0, count($params), '?'));
/*
    Ce morceau de code va préparer la requête avec assez de marqueurs pour chaque valeur
    du tableau $params. Les valeurs du tableau $params sont ensuite liées aux marqueurs
    de la requête préparée lorsque la requête est exécutée. Ce n'est pas la même chose
    que d'utiliser la méthode PDOStatement::bindParam() sachant qu'elle impose une
    référence vers les valeurs. La méthode PDOStatement::execute() ne fait que lier
    par la valeur.
*/
$sth = $dbh->prepare("SELECT id, name FROM contacts WHERE id IN ($place_holders)");
$sth->execute($params);
```



