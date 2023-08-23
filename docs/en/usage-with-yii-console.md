# Yii Console

Example using [yiisoft/app](https://github.com/yiisoft/app).

Di-Container:

Create `config/common/db.php` with content:
```php
<?php

declare(strict_types=1);

use Yiisoft\Db\Connection\ConnectionInterface;
use Yiisoft\Db\Sqlite\Connection as SqliteConnection;

return [
    ConnectionInterface::class => [
        'class' => SqliteConnection::class,
        '__construct()' => [
            'dsn' => 'sqlite:' . __DIR__ . '/Data/yiitest.sq3'
        ]
    ]
];
```

Add to `config/params.php`:
```php
...
'yiisoft/yii-db-migration' => [
    'createNamespace' => 'App\\Migration',
    'updateNamespaces' => ['App\\Migration'],
],
...
```

Now the `MigrationService::class` uses the `View` of the application that is already registered in `yiisoft/view`.

Execute `composer du` in console config its rebuild.

Now we have the `yiisoft/yii-db-migration` package configured and it can be called in the console.

View the list of available commands execute in console: `./yii list`

```shell
./yii list
```