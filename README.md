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

Create Epic allows you to create a new Epic in Clubhouse. See [complete list of available fields](https://clubhouse.io/api/v1/#create-epic).

```php
$new_epic = [
    'deadline' => '2020-08-16T12:30:00Z',
    'name' => 'Terraforming of Mars',
    'description' => 'Should be easy. Couple of astropeople, a trowel each. Easy.'
];

$epic = $clubhouse->create('epics', $new_epic);
```

## Files

### Get

Get File returns information about the selected File.

```php
$file_id = '3000';

$file = $clubhouse->get('files', $file_id);
```
### Update

Update File can used to update the properties of a file uploaded to Clubhouse. See [complete list of available fields](https://clubhouse.io/api/v1/#update-file).

```php
$file_id = "4351";

$data = [
    'description' => 'This file contains all of my most important passwords, in plain text.',
    'name' => 'Paswords.txt'
];

$update = $clubhouse->update('files', $file_id, $data);
```

### Delete

Delete File can be used to delete any previously attached File.

```php
$file_id = '3000';

$clubhouse->delete('files', $file_id);
```

### List

List Files returns a list of all Files and related attributes in your Clubhouse.

```php
$files = $clubhouse->get('files');
```

## Labels

### Create

Create Label allows you to create a new Label in Clubhouse.

```php
$new_label = [
    'external_id' => 'thirdparty-id-123',
    'name' => 'My New Label'
];

$label = $clubhouse->create('labels', $new_label);
```

### Update

Update Label allows you to replace a Label name with another name. If you try to name a Label something that already exists, you will receive a 422 response.

```php
$label_id = "1234";

$data = [
    'name' => 'Updated Label Name'
];

$label = $clubhouse->update('labels', $label_id, $data);
```

### Delete

Delete Label can be used to delete any Label.

```php
$label_id = '3000';

$clubhouse->delete('labels', $label_id);
```

### List

List Labels returns a list of all Labels and their attributes.

```php
$labels = $clubhouse->get('labels');
```

## Linked-Files

### Get

Get File returns information about the selected Linked File.

```php
$link_id = 5000;

$linked_files = $clubhouse->get('linked-files', $link_id);
```

### Create

Create Linked File allows you to create a new Linked File in Clubhouse. See [complete list of available fields](https://clubhouse.io/api/v1/#create-linked-file)

```php
$new_link = [
    'name' => 'My Linked File',
    'description' => 'Description of the file',
    'type' => 'dropbox',
    'url' => 'http://dropbox.com/1sjsSA9Q/asd20j.txt
];

$linked_file = $clubhouse->create('linked-files', $new_link);
```

### Update

Updated Linked File allows you to update properties of a previously attached Linked-File. See [complete list of available fields](https://clubhouse.io/api/v1/#update-linked-file)

```php
$link_id = "1234";

$data = [
    'name' => 'New name for linked file',
    'description' => 'Description of new linked file'
];

$linked_file = $clubhouse->update('linked-files', $link_id, $data);
```

### Delete

Delete Linked File can be used to delete any previously attached Linked-File.

```php
$link_id = '3000';

$clubhouse->delete('linked-files', $link_id);
```

### List

List Linked Files returns a list of all Linked-Files and their attributes.

```php
$linked_files = $clubhouse->get('linked-files');
```

## Projects

### Get 

Get Project returns information about the selected Project.

```php
$project_id = '2990';

$project = $clubhouse->get('projects', $project_id);
```

### Create

Create Project is used to create a new Clubhouse Project. See [complete list of available fields](https://clubhouse.io/api/v1/#create-project)

```php
$new_project = [
    'name' => 'New Clubhouse Project',
    'description' => 'Description of the project',
    'abbreviation' => 'ncp'
];

$project = $clubhouse->create('projects', $new_project);
```

### Update 

Update Project can be used to change properties of a Project.  See [complete list of available fields](https://clubhouse.io/api/v1/#update-project)

```php
$project_id = "1234";

$data = [
    'name' => 'New name for project',
    'description' => 'Description update text'
];

$project = $clubhouse->update('projects', $project_id, $data);
```

### Delete

Delete Project can be used to delete a Project. Projects can only be deleted if all associated Stories are moved or deleted. In the case that the Project cannot be deleted, you will receive a 422 response.

```php
$project_id = '3000';

$clubhouse->delete('projects', $project_id);
```

### List

List Projects returns a list of all Projects and their attributes.

```php
$projects = $clubhouse->get('projects');
```

## Story-Links

### Create

Story links allow you create semantic relationships between two stories. Relationship types are relates to, blocks / blocked by, and duplicates / is duplicated by. The format is subject -> link -> object, or for example “story 5 blocks story 6”. See [complete list of available fields](https://clubhouse.io/api/v1/#create-story-link)

```php
$new_link = [
    'object_id' => 100,
    'subject_id' => 250,
    'verb' => 'blocks' //blocks, relates, duplicates
];

$story_links = $clubhouse->create('story-links', $new_link);
```

### Get

Returns information about the selected Story Link.

```php
$storylink_id = '3000';

$story_links = $clubhouse->get('story-links', $storylink_id);
```

### Delete

Delete Story-Link can be used to delete any Story Link.

```php
$storylink_id = '3000';

$clubhouse->delete('story-links', $storylink_id);
```

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

