#array

```php

/* Exécute une commande préparée en utilisant un tableau de valeurs pour les clauses IN */
$params = array(1, 21, 63, 171);
/* Crée une chaîne pour les marqueurs */
$place_holders = implode(',', array_fill(0, count($params), '?'));
/*
    Ce morceau de code va préparer la requête avec assez de marqueurs pour chaque valeur
    du tableau $params. Les valeurs du tableau $params sont ensuite liées aux marqueurs
    de la requête préparée lorsque la requête est exécutée. Ce n'est pas la même chose
    que d'utiliser la méthode PDOStatement::bindParam() sachant qu'elle impose une
    référence vers les valeurs. La méthode PDOStatement::execute() ne fait que lier
    par la valeur.
*/
$sth = $dbh->prepare("SELECT id, name FROM contacts WHERE id IN ($place_holders)");
$sth->execute($params);

```

#user.ini


```php

error_reporting = E_ALL
log_errors = On
display_errors = On
```


#requetes

```php
$pdo->prepare("DELETE FROM users")->execute();
```


```php
$where = ['id' => 1];
$pdo->prepare("DELETE FROM users WHERE id=:id")->execute($where);
```



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



```php
//With fetch for large results.
$stmt = $pdo->prepare("SELECT * FROM employees WHERE name = :name");
$stmt->execute(['name' => $name]);

foreach ($stmt as $row) {
    // do something with $row
}

//With fetchAll for small results.

$news = $pdo->query('SELECT * FROM news')->fetchAll();
```




```php
$stmt = $pdo->prepare("SELECT * FROM users WHERE email = :email AND status=:status LIMIT 1");
$stmt->execute(['email' => $email, 'status' => $status]);
$user = $stmt->fetch();
```





```php
$host = '127.0.0.1';
$dbname = 'test';
$username = 'root';
$password = '';
$charset = 'utf8';
$collate = 'utf8_unicode_ci';
$dsn = "mysql:host=$host;dbname=$dbname;charset=$charset";
$options = [
    PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
    PDO::ATTR_PERSISTENT => false,
    PDO::ATTR_EMULATE_PREPARES => false,
    PDO::ATTR_DEFAULT_FETCH_MODE => PDO::FETCH_ASSOC,
    PDO::MYSQL_ATTR_INIT_COMMAND => "SET NAMES $charset COLLATE $collate"
];

$pdo = new PDO($dsn, $username, $password, $options);
```




