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