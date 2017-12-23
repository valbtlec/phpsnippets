

\# test \#



\`\`\`php

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

 

\`\`\`

