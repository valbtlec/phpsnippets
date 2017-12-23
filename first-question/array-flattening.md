```php
$array =[
  'name' =>[
    'val',
    'Psy'
    ],
    'hobbies =>[
    'dev',
    'fitness'
    ]
    'color'=>[
    'blue'
    ]
 
];
 
$flattened= new RecursiveArrayIterator($array);
$flattened= new RecursiveIteratorIterator($flattened);
$flattened= iterator_to_array($flattened, false);
 
 
//shorter
$flattened=iterator_to_array(new RecursiveIteratorIterator(new RecursiveArrayIterator($array),false);
 
```