

```php
$dsn = "mysql:host=localhost;dbname=btlec";
try
{
$pdo = new PDO($dsn, 'root', '');
}
catch (PDOException $exception)
{
exit('Erreur de connexion BDD');
}


$sql = "SELECT date,id,file,category,week(date) as week FROM gazette ORDER BY date";
$result = $pdo->query($sql);
while ($row = $result->fetch()) {
                $results[] = array(
                    'id' => $row['id'],
                    'date' => $row['date'],
                    'file' => $row['file'],
                    'category' => $row['category'],
                    'week' => $row['week'],
                     
        );
    }

?>    
<table border="1" cellpadding="2px">
 <thead>
      <tr>
          <th bgcolor="#CECECE">Date</th>
          <th bgcolor="#CECECE">Candidates Added</th>
          <th bgcolor="#CECECE">Candidates Edited</th>
          <th bgcolor="#CECECE">Notes Added</th>
          <th bgcolor="#CECECE">Candidates Forwarded</th>
      </tr>
   </thead>
   <tbody>
<?php   
    for ($i=0;$i<count($results);$i++){
    ?>
    <tr>
          <td><center><?php echo $results[$i]['id'] ?></center></td>
          <td><center><?php echo $results[$i]['date'] ?></center></td>
          <td><center><?php echo $results[$i]['file'] ?></center></td>
          <td><center><?php echo $results[$i]['category'] ?></center></td>
          <td><center><?php echo $results[$i]['week'] ?></center></td>
  </tr>

<?php   
    }
?>
```

