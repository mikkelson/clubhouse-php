# Clubhouse.io REST API PHP Wrapper

This is a lightweight PHP wrapper for the Clubhouse.io REST version 1 API.

## Installation

To install **with Composer**:

```
composer require mikkelson/clubhouse-php
```

After the package installation completes, use the autoloader provided by Composer.

```php
require __DIR__ . '/vendor/autoload.php';
```

Or, **without Composer**:

Download this repo and include Clubhouse.php

```php
include('src/Clubhouse.php');
```

## Usage & Setup

Load the package namespace.

```php
use Mikkelson\Clubhouse;
```

Before making useful calls to Clubhouse, create an instance of `Clubhouse`, providing your Clubhouse API token, which you can get [here](https://app.clubhouse.io/settings/account/api-tokens).

```php
    
    $token = '213901-dk9AJ-3SOJ-8dj9-KAAa0smsa';
    $clubhouse = new Clubhouse($token);

```

## Epics

### Get

```php
//Return an array of all Epics
$epics = $clubhouse->get('epics');

//Return specific epic, as an array
$epic_id = 'JDaa9k-29d3-40s2-a4dc-a9bsd29sc';
$epic = $clubhouse->get('epic', $epic_id);
```

### Update
### Delete
### List
### Create

## Files

### Get
### Update
### Delete
### List

## Labels

### Get
### Update
### Delete
### List

## Linked-Files

### Get
### Update
### Delete
### List
### Create

## Projects

## Story-Links

## Stories

## Users

### Get

```php
//Return an array of all Uusers
$users = $clubhouse->get('users');

//Return specific user , as an array
$user_id = '4JDaa9k-29d3-40s2-a4dc-a9bsd29sc';
$user = $clubhouse->get('users', $user_id);
```

## Workflows

