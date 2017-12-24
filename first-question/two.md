#multidimentional arrays
 
##rechercher une valeur

*array exemple : *

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

  * avec array_search et array_column

```php
$found_key = array_search('blue', array_column($people, 'fav_color'));  // retour 5, l'id de l'array et non l'emplacement dans le tableau
```


	$name= $people[$found_key]['name']; // le nom de l'array 5 =>samuel
