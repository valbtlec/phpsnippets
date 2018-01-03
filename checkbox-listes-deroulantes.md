

 * récupérer les valeur des cases cochées

recup valeur checkbox => array en name

```html
<form method="POST" action="checkbox.php">
    <input type="checkbox" name="choix[]" value="1"> nom 1<br>
    <input type="checkbox" name="choix[]" value="2"> nom 2<br>
    <input type="checkbox" name="choix[]" value="3"> nom 3<br>
     <input type="submit" value="test">
</form>
```

```php
if(!empty($_POST['choix']))
{
echo 'Les valeurs des cases cochées sont :<br />';
foreach($_POST['choix'] as $val)
{
echo $val,'<br />';
}
echo '<br />
```
 * récupérer valeur liste déroulante
 


```html
<form action ="indexplanification.php" method="post">
<select name="page">
<option value='valeur1'>un</option>
<option value='valeur2'>deux</option>
<input type="submit" name ="choixafficheur" value="Selectionner">
<?php
if(isset($_POST['choixafficheur'])){
 $afficheur=$_POST['page'];
}



```

 * alimenter automatiquement des listes déroulantes et récupérer les valeurs séléctionnées



```html
<form method="POST" action="checkbox.php">
 <select name='datePrime'>
 <?php
 for($i=0;$i<sizeOf($tabDatePrime); $i++)
 {
    echo "<OPTION value='".$tabDatePrime[$i]."'><a href='".$tabNomFichier[$i]."'>".$tabDatePrime[$i]. "</a></OPTION>";
 }
?>
 </select>
<input type='submit' name='consultationok' value='Indexer'> 
</form>
 <?php
 if(isset($_POST['consultationok']))
 {
  $periode=$_POST['datePrime'];
  echo $periode;
 }
 else
 {
 echo 'bouton non valide';
 }
```


 ?>