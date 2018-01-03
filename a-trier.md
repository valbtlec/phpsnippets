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

##delete
```php
$pdo->prepare("DELETE FROM users")->execute();
```


```php
$where = ['id' => 1];
$pdo->prepare("DELETE FROM users WHERE id=:id")->execute($where);
```


##update
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


##insert
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


##select
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

##close cursor


```php
$reponse->closeCursor();
```




##connect


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



```php
$config = array(
    'host'      => 'localhost',
    'port'      => 8889, // 3306
    'username'  => 'root',
    'password'  => 'root',
    'database'  => 'oracom',
);
//		/functions/database.fn.php
function getPDOLink($config) {
	$dsn = 'mysql:dbname='.$config['database'].';host='.$config['host'].';port='.$config['port'];
	try {
		return new PDO($dsn, $config['username'], $config['password']);
	} catch (PDOException $exception) {
		exit('BDD Error Connection');
	}
}
```



```
$dsn = "mysql:host=localhost;dbname=pagination;port=8889;charset=utf8";
try 
{
    $pdo = new PDO($dsn, 'root', 'root');
} 
catch (PDOException $exception) 
{
    mail('mon-adresse-mail@mail.fr', 'PDOException', $exception->getMessage());
    exit('Erreur de connexion BDD');
}
```





#form



```php
<!-- sécuriser le php self -->
<form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]);?>">
```



