#multidimentional arrays
 
##rechercher une valeur

*arrays exemples : *

**array people avec clés qui ne se suivent pas**

```php
$people = array(
  2 => array(
    'name' => 'John',
    'fav_color' => 'green'
  ),
  5=> array(
    'name' => 'Samuel',
    'fav_color' => 'blue'
  ),
    7=> array(
    'name' => 'val',
    'fav_color' => 'black'
  )
);
```

**array services avec clés qui se suivent et commencent à 0 (requete pdo, les tableaux ordonnés) : **

```php
$services = array(
	0 => array(
		'id' => 15,
		'full_name' => 'green'
	),
	1=> array(
		'id' => 5,
		'full_name' => 'blue'
	),
	2=> array(
		'id' => 2,
		'full_name' => 'black'
	),
	3=> array(
		'4' => 2,
		'full_name' => 'yellow'
	)
);
```


* recherche avec array_search et array_column
  * cas 1 - tableau ordonné


```php
$idtab = array_search(5, array_column($services, 'id'));  
// retourne 1 , l'id de l'array et non l'emplacement dans le tableau

$service= $services[$idtab]['full_name']; // blue

```

   * cas 2 - tableau non ordonné

```php
$found_key = array_search('blue', array_column($people, 'fav_color'));  
// retour 5, l'id de l'array et non l'emplacement dans le tableau
```

du coup :

```php
//renvoi une erreur car cherche $people[5] qui n'existe pas
$name= $people[$found_key]['name']; // le nom de l'array 5 =>samuel

```





  * utilisation d'une fonction récursive

```php
function recursive_array_search($needle,$haystack) {
    foreach($haystack as $key=>$value) {
        $current_key=$key;
        if($needle===$value OR (is_array($value) && recursive_array_search($needle,$value) !== false)) {
            return $current_key;
        }
    }
    return false;
}
echo $result=recursive_array_search('blue',$people); // attention renvoi  cette fois ci
```

  
