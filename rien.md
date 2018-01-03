* utilisation de md5 pour générer un nom de fichier aléatoire




```php
$filename = $_FILES[$uploadfile]['name'];
$save_path = '/var/domainame/uploads/'; # Outside of web root
$extension = end(explode('.', $filename)); #extension of the file
$renamed = md5($filename. time());        #rename of the file
if (!@move_uploaded_file($_FILES[$uploadfile]['tmp_name'], $save_path.$renamed. $extension)) 
{
    echo 'File could not be saved.';
    exit(0);
}
```

