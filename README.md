# DBAL

DataBase Abstraction Layer.

### Installation

The package can be installed via Composer by requiring the "artoodetoo/dbal" package in your project's composer.json.

```json
{
    "require": {
        "artoodetoo/dbal": "dev-master"
    }
}
```

### Usage

```php
require 'vendor/autoload.php';

use R2\DBAL\PDOMySQL;

$db = new PDOMySQL([
    'username' => 'john',
    'password' => 'tiger',
    'dbname'   => 'testdb'
]);
$list = $db
    ->query("SELECT id FROM test")
    ->fetchAssocAll();
```

### Feature list

Every DBALInterface descendant do:
  * named placeholders without ":" sign, so you can do
```php
    $db->query($sql, compact('name', 'city', 'ids'))
```
  * array substitution for IN(:ids)
  * auto NULL substitution for nulls or empty arrays
  * method chaining like
```php
    $db
        ->beginTransaction
            ->query($insertSql1)
            ->query($insertSql2)
            ->query($insertSql3)
        ->commit();
```

### License

The DBAL is open-source software, licensed under the [MIT license](http://opensource.org/licenses/MIT)
