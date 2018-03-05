
```php

// permet de faire la différence entre répertoire et fichier
$dir='D:\www\_intranet\upload\2018bookfdm';

function scanIt($dir){
$iterator= new DirectoryIterator($dir);
foreach ($iterator as $value)
{
if(!$value->isDot())
{
if($value->getType()=="dir")
{
echo "<p class='dir'>". $value->getFilename().'</p>';
scanIt($dir . DIRECTORY_SEPARATOR. $value);
}
else
{
echo $value->getFilename().'<br>';
}
}

}
}
scanIt($dir);

```

