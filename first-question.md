#trier les tableaux multidimentionnels

1-fonction pour tableaux renvoyés par pdo
2- tri d'un tableau multi avec un nombre d'index limités
(voir la doc : http://php.net/manual/fr/function.array-multisort.php)


1- **fonction spéciale pour les tableau multi renvoyés par pdo**

```php
//fonction
function array_msort($array, $cols)
{
    $colarr = array();
    foreach ($cols as $col => $order) {
        $colarr[$col] = array();
        foreach ($array as $k => $row) { $colarr[$col]['_'.$k] = strtolower($row[$col]); }
    }
    $eval = 'array_multisort(';
    foreach ($cols as $col => $order) {
        $eval .= '$colarr[\''.$col.'\'],'.$order.',';
    }
    $eval = substr($eval,0,-1).');';
    eval($eval);
    $ret = array();
    foreach ($colarr as $col => $arr) {
        foreach ($arr as $k => $v) {
            $k = substr($k,1);
            if (!isset($ret[$k])) $ret[$k] = $array[$k];
            $ret[$k][$col] = $array[$k][$col];
        }
    }
    return $ret;

}


//exemple


$arr1 = array(
    array('id'=>1,'name'=>'aA','cat'=>'cc'),
    array('id'=>2,'name'=>'aa','cat'=>'dd'),
    array('id'=>3,'name'=>'bb','cat'=>'cc'),
    array('id'=>4,'name'=>'bb','cat'=>'dd')
);

$arr2 = array_msort($arr1, array('name'=>SORT_DESC, 'cat'=>SORT_ASC));

debug($arr1, $arr2);

```

**2-nombre limité de tableau**



```
$ar = array(
       array("10", 11, 100, 100, "a"),
       array(   1,  2, "2",   3,   1)
      );
array_multisort($ar[0], SORT_ASC, SORT_STRING,
                $ar[1], SORT_NUMERIC, SORT_DESC);
var_dump($ar);
```

