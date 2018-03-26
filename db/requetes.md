# REQUETES

## SELECT - BASIC

```php
function infoService($db){
	$req=$pdo->prepare('SELECT * FROM services WHERE slug = :gt');
	$req->execute(array(
	':gt' =>$_GET['gt']
	));
	return $row=$req->fetchAll(PDO::FETCH_ASSOC);
}
```

## INSERT - BASIC

```php
function recordReply($pdoBt,$idMsg,$file)
{
	$date=new DateTime();
	$date=$date->format('Y-m-d H:i:s');
	$reply=strip_tags($_POST['reply']);
	$reply=nl2br($reply);
	$insert=$pdoBt->prepare('INSERT INTO replies (id_msg, reply, replied_by, date_reply,inc_file) VALUE (:id_msg, :reply, :replied_by, :date_reply, :inc_file)');
	$result=$insert->execute(array(
		':reply'		=> $reply,
		':date_reply'		=> $date,
		':id_msg'		=> $idMsg,
		':replied_by'		=>$_SESSION['id'],
		':inc_file'		=> $file
	));
	return $result;
}
```


## UPDATE - BASIC


```php
function affectation($pdoBt,$idMsg,$service)
{
	$update=$pdoBt->prepare('UPDATE msg SET id_service= :service  WHERE id= :id');
	$result=$update->execute(array(
		':service'		=> $service,
		':id'		=>$idMsg
	));
	return $result;
}
```





## delete -2

```php
$pdo->prepare("DELETE FROM users")->execute();
```

```php
$where = ['id' => 1];
$pdo->prepare("DELETE FROM users WHERE id=:id")->execute($where);
```

## update -2

```php
$row = [
'updated_at' => '2017-01-01 00:00:00'
];
$sql = "UPDATE users SET updated_at=:updated_at";
$pdo->prepare($sql)->execute($row);

$affected = $pdo->rowCount();
```

```php
$row = [
'id' => 1,
'username' => 'bob',
'email' => 'bob2@example.com'
];
$sql = "UPDATE users SET username=:username, email=:email WHERE id=:id;";
$status = $pdo->prepare($sql)->execute($row);
```

```php
function updateTodo(PDO $pdo, $todo) {
$sql = "UPDATE todo SET name = :name, content = :content WHERE id = :id";
$prepare = $pdo->prepare($sql);
return $prepare->execute(array(
'id' => $todo['id'],
'name' => $todo['name'],
'content' => $todo['content'],
));
}
```

## insert -2

```php
$row = [
'username' => 'bob',
'email' => 'bob@example.com'
];
$sql = "INSERT INTO users SET username=:username, email=:email;";
$status = $pdo->prepare($sql)->execute($row);

if ($status) {
$lastId = $pdo->lastInsertId();
echo $lastId;
}
```

## select -2

```php
//With fetchALL for large results.
$stmt = $pdo->prepare("SELECT * FROM employees WHERE name = :name");
$stmt->execute(['name' => $name]);

foreach ($stmt as $row) {
// do something with $row
}

//With fetch for small results.

$news = $pdo->query('SELECT * FROM news')->fetch();



```php
// compter le nombre de résultats :

$stmt->rowCount()
```




function findTodo(PDO $pdo, $id) {
$sql = "SELECT * FROM todo WHERE id = {$pdo->quote($id, PDO::PARAM_INT)}"; //Représente le type de données INTEGER SQL
$query = $pdo->query($sql);
if ($query) {
return $query->fetch(PDO::FETCH_ASSOC);
} else {
return false;
}
}
```

```php
$stmt = $pdo->prepare("SELECT * FROM users WHERE email = :email AND status=:status LIMIT 1");
$stmt->execute(['email' => $email, 'status' => $status]);
$user = $stmt->fetch();
```

## close cursor

```php
$reponse->closeCursor();
```# requetes

## delete

```php
$pdo->prepare("DELETE FROM users")->execute();
```

```php
$where = ['id' => 1];
$pdo->prepare("DELETE FROM users WHERE id=:id")->execute($where);
```

##rowcount


```php
	$rowCount=$req->rowCount();
```

