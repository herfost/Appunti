# Snippets PHP

## Connessione al database
Documentazione:
- [mysqli_connect](https://www.php.net/manual/en/mysqli.construct.php)
- [mysqli_connect_errno](https://www.php.net/manual/en/mysqli.connect-errno.php)
- [mysqli_connect_error](https://www.php.net/manual/en/mysqli.connect-error.php)

In `database.php`:
```php
<?php
define('DB_NAME', 'db0');
define('HOST', 'localhost');
define('PASSWORD', 'admin'); 

$connection =  mysqli_connect(DB_NAME, HOST, PASSWORD, null);
if (!$connection) {
    echo "Error: Unable to connect to MySQL." . PHP_EOL;
    echo "Debugging errno: " . mysqli_connect_errno() . PHP_EOL;
    echo "Debugging error: " . mysqli_connect_error() . PHP_EOL;
    exit;
}
```

## Login
Documentazione:
- [session_start](https://www.php.net/manual/en/function.session-start.php)
- [sha1](https://www.php.net/manual/en/function.sha1.php)
- [mysqli_query](https://www.php.net/manual/en/mysqli.query.php)
- [mysql_num_rows](https://www.php.net/manual/en/function.mysql-num-rows.php)
- [header](https://www.php.net/manual/en/function.header.php)

In `login-page.php`:
```php

<?php if ( !$_SESSION['logged-in'] ): ?>
<form action="login.php" method="post">
    <input type="text" name="username">
    <input type="password" name="password">
    <input type="submit" name="send-login">
</form> 
...
<?php endif; ?>

```

In `login.php`:
```php
<?php
include './database.php';
session_start();
$location = 'index.php';

$username = isset($_POST['username']) ? $_POST['username'] : false;
$password = isset($_POST['password']) ? sha1( htmlspecialchars($_POST['password']) ) : false;

if ( !($username || $password) ) die("Username and password"); 

$query = "SELECT * FROM users WHERE username = `$username` AND password = `password`";
$authentication = mysqli_query($connection, $query);
$_SESSION['logged_in'] = mysql_num_rows($authentication) > 0;

header('Location: $location');
```