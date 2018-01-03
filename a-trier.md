# array



# user.ini

```php
error_reporting = E_ALL
log_errors = On
display_errors = On
```


# form

```php
<!-- sécuriser le php self -->
<form method="post" action="<?php echo htmlspecialchars($_SERVER["PHP_SELF"]);?>">
```

# email validation

```php
if(!filter_var($_POST["email"],FILTER_VALIDATE_EMAIL))
{
    $error_mail="email erroné";
    $error=true;
}
else
{
    $email=$_POST["email"];
}
```



