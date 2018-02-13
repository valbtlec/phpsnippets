# requetes

## delete

```php
$pdo->prepare("DELETE FROM users")->execute();
```

```php
$where = ['id' => 1];
$pdo->prepare("DELETE FROM users WHERE id=:id")->execute($where);
```

## update

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

## insert

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

## select

```php
//With fetchALL for large results.
$stmt = $pdo->prepare("SELECT * FROM employees WHERE name = :name");
$stmt->execute(['name' => $name]);

foreach ($stmt as $row) {
// do something with $row
}

//With fetch for small results.

$news = $pdo->query('SELECT * FROM news')->fetch();


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
