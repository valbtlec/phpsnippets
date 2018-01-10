#upload


## upload multi fichiers

 * penser à l'attribut enctype dans le form
 * passer un tableau dans le name pour récupérer TOUT les fichiers
 * attribut multiple dans le input file
 
```php
<form action="" method="post" enctype="multipart/form-data">
<input type="file" multiple="multiple" name="uploadFiles[]" />
```

