

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

 * alimentation case à cocher avec db :


```php
 echo "<input type='checkbox' class='filled-in' id='".$service['id']."' name='service[]' value= '".$service['id']."' />";
 echo "<label for='".$service['id']."'>".$service['full_name']."</label>";
 
 //renvoi la valeur de value de la case cochée
$newService=$_POST['service'][0];

 
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
* fonction d'alimentation une liste déroulante via requete sql


```php
function fill_unit_select_box($connect)
{ 
 $output = '';
 $query = "SELECT * FROM tbl_unit ORDER BY unit_name ASC";
 $statement = $connect->prepare($query);
 $statement->execute();
 $result = $statement->fetchAll();
 foreach($result as $row)
 {
  $output .= '<option value="'.$row["unit_name"].'">'.$row["unit_name"].'</option>';
 }
 return $output;
}
 
// dans le form :

 echo fill_unit_select_box($connect) 
 
```


* liste déroulante : sélectionner par défaut la valeur du champ récupéré de la db



```php
<select class="form-control" id="gt" name="gt">
<option value="brun" <?=$odr['gt']=='brun' ? ' selected="selected"' : '' ?>>BRUN</option>
<option value="gem" <?=$odr['gt']=='gem' ? ' selected="selected"' : '' ?> >GEM</option>
<option value="gris" <?=$odr['gt']=='gris' ? ' selected="selected"' : '' ?> >GRIS</option>
<option value="pem" <?=$odr['gt']=='pem' ? ' selected="selected"' : '' ?> >PEM</option>
</select>
```


