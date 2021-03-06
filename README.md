# NoSQLite – simple key => value store based on SQLite3

[![Build Status](https://secure.travis-ci.org/mthenw/nosqlite.php.png)](https://travis-ci.org/mthenw/nosqlite.php)
[![Coverage Status](https://coveralls.io/repos/mthenw/nosqlite.php/badge.png?branch=master)](https://coveralls.io/r/mthenw/nosqlite.php?branch=master)
[![Latest Stable Version](https://poser.pugx.org/mthenw/nosqlite/v/stable.png)](https://packagist.org/packages/mthenw/nosqlite)

## Introduction

NoSQLite is simple key-value store using SQLite as raw data store. Mainly for small project where MySQL is too heavy and files are too ugly.

## Requirements

- PHP >=5.3.2
    - PDO (by default as of PHP 5.1.0)
    - PDO_SQLITE (by default as of PHP 5.1.0)

## Installing via Composer

[Get composer](http://getcomposer.org/download/) and add following lines to ```composer.json```:
```
{
    "require": {
        "mthenw/nosqlite": "*@stable"
    }
}
```

## Usage

1. Create stores' manager (file will be created if not exists)

        $nsql = new NoSQLite\NoSQLite('mydb.sqlite');

2. Get store

        $store = $nsql->getStore('movies');

3. Set value in store (key and value max length are [limited by SQLite TEXT datatype](http://sqlite.org/limits.html#max_length))

        $store->set(uniqid(), json_encode(array('title' => 'Good Will Hunting', 'director' => 'Gus Van Sant'));

4. Get value from store (will be created if not exists)

        $store->get('3452345');

5.  Get all values

        $store->getAll();

6. Delete all values

        $store->deleteAll();

7. Iterate through store (Store implements Iterator interface)

        foreach($store as $key => $value)
            ...

8. Get number of values in store (Store implements Countable interface)

        count($store);

## Tests

Tests are written in PHPUnit which is required as a dev package in ```composer.json```. For running test use

    ./vendor/bin/phpunit

or simply

    make test

