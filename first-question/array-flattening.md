$array =\[

  'name' =&gt;\[

    'val',

    'Psy'

    \],

    'hobbies =&gt;\[

    'dev',

    'fitness'

    \]

    'color'=&gt;\[

    'blue'

    \]

 

\];

 

$flattened= new RecursiveArrayIterator\($array\);

$flattened= new RecursiveIteratorIterator\($flattened\);

$flattened= iterator\_to\_array\($flattened, false\);

 

 

//shorter

$flattened=iterator\_to\_array\(new RecursiveIteratorIterator\(new RecursiveArrayIterator\($array\),false\);

```
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



