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

Get Epic returns information about the selected Epic.

```php
$epic_id = '3000';
$epic = $clubhouse->get('epics', $epic_id);
```

### Update

Update Epic can be used to update numerous fields in the Epic. See [complete list of available fields](https://clubhouse.io/api/v1/#update-epic).

```php
$epic_id = "4351";
$data = [
    'description' => 'Keep your developers happy by providing detailed descriptions (-;',
    'state' => 'to do'
];
$update = $clubhouse->update('epics', $epic_id, $data);
```

### Delete

Deletes an Epic


```php
$epic_id = '3000';
$clubhouse->delete('epics', $epic_id);
```

### List

List Epics returns a list of all Epics and their attributes.

```php
$epics = $clubhouse->get('epics');
```

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

### List

List Users returns information about users in the organization.

```php
$users = $clubhouse->get('users');
```

### Get

Returns information about a User.

```php
$user_id = '4JDaa9k-29d3-40s2-a4dc-a9bsd29sc';
$user = $clubhouse->get('users', $user_id);
```

## Workflows

### List

List Workflows returns a list containing the single Workflow in the organization and its attributes.

```php
$workflows = $clubhouse->get('workflows');
```

