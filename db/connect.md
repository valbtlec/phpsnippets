## connect

 * avec des constantes 
 

```php

try{
     $pdo=new PDO("mysql:host=localhost;dnbame=mabase", "root", "");
 }
 catch(PDOException $e){
     die('Erreur: ' .$e->getMessage());
 }

//devient :
define('DB_HOST', 'localhost');
define('DB_NAME', 'btlec');
define('DB_USER', 'root');
define('DB_PASSWORD', '');    
    
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

```php
$config = array(
    'host'      => 'localhost',
    'port'      => 8889, // 3306
    'username'  => 'root',
    'password'  => 'root',
    'database'  => 'oracom',
);
//        /functions/database.fn.php
function getPDOLink($config) {
    $dsn = 'mysql:dbname='.$config['database'].';host='.$config['host'].';port='.$config['port'];
    try {
        return new PDO($dsn, $config['username'], $config['password']);
    } catch (PDOException $exception) {
        exit('BDD Error Connection');
    }
}
```

```php
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

