

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



 * alimenter automatiquement des checkbox et récupérer les valeurs cochées

<form method="POST" action="checkbox.php">

 <?php
 echo "<select name='datePrime'>";
for($i=0;$i<sizeOf($tabDatePrime); $i++){
	echo "<OPTION value='".$tabDatePrime[$i]."'><a href='".$tabNomFichier[$i]."'>" .$tabDatePrime[$i]. "</a></OPTION>";

}
echo "</select>";
 echo"<input type='submit' name='consultationok' value='Indexer'> </form>";
 if(isset($_POST['consultationok'])){
 $periode=$_POST['datePrime'];
 echo $periode;
 echo 'bouton valide';
 }
 else
 {
 echo 'bouton non valide';
 }
 ?>