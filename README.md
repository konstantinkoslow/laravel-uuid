# Laravel UUID

Trait for generating UUID primary keys for Laravel version 5.6 and higher.

## Installation

Install the package via Composer:

```shell
composer require konstantinkoslow/laravel-uuid
```

## Usage

### Laravel Migrations

To let a Model make use of UUIDs as primary key, you have to add a UUID field in your migration file and set this as primary key:

```php
Schema::create('table_name', function (Blueprint $table) {
    $table->uuid('id');
    $table->primary('id');

    // or

    $table->char('key', 36)->primary();
});
```

> Eloquent will also assume that each table has a primary key column named `id`. You may define a protected `$primaryKey` property to override this convention.

For example:

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class ModelName extends Model
{
    protected $primaryKey = 'key';
}
```

Read more [Laravel - Eloquent Model Conventions](https://laravel.com/docs/5.6/eloquent#eloquent-model-conventions).

### Eloquent Model

Bind the traid with the `use` operator into the Model that uses UUIDs as primary key:

```php
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;
use KonstantinKoslow\LaravelUuid\UsesUuid;

class ModelName extends Model
{
    use UsesUuid;
}
```

## License

Laravel UUID is licensed under the [MIT license](https://opensource.org/licenses/MIT).