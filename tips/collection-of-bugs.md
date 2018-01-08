#bugs 


 * end() - explode():


```php
 $file_name = $_FILES[$upload_name]['name'];
 $file_extension = end(explode('.', $file_name)); 
```


 // renvoie l'erreur : Only variables should be passed by reference in php file name
    
**explication : ** end requires a reference, because it modifies the internal representation of the array (i.e. it makes the current element pointer point to the last element).

**The result of explode('.', $file_name) cannot be turned into a reference. This is a restriction in the PHP language, that probably exists for simplicity reasons.**

**solution : ** passer par une variable intermédiaire :


```php
$filename=$_FILES['file']['name'];
$tmp=explode('.',$filename);
$ext=end($tmp);
$filename= md5(time()).'.'.$ext;
```

