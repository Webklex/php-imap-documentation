---
title: Client
---

## Connect to the server
Every client has to connect to the server before any operation can be performed.

```php
/** @var \Webklex\PHPIMAP\Client $client */

$client->connect();
```


## Get the connection status
Check if the current connection is still established.

```php
/** @var \Webklex\PHPIMAP\Client $client */
/** @var boolean $status */

$status = $client->isConnected();
```


## Check the current connection
Check if the current connection is still alive and reconnect if necessary.

```php
/** @var \Webklex\PHPIMAP\Client $client */

$client->checkConnection();
```


## Force reconnect
You can force the client to do a reconnect. This will close the connection and open a new one.

```php
/** @var \Webklex\PHPIMAP\Client $client */

$client->reconnect();
```


## Close connection
You can force the client to close the current connection.

```php
/** @var \Webklex\PHPIMAP\Client $client */

$client->disconnect();
```


## List all available folders
If hierarchical order is set to true, it will make a tree of folders, otherwise it will return flat array.

```php
/** @var \Webklex\PHPIMAP\Client $client */
/** @var \Webklex\PHPIMAP\Support\FolderCollection $folders */

$folders = $client->getFolders($hierarchical = true);
```

## Find a folder by path
Provide the entire folder path. Your delimiter may vary.

```php
/** @var \Webklex\PHPIMAP\Client $client */
/** @var \Webklex\PHPIMAP\Folder $folder */

$folder = $client->getFolderByPath('INBOX.name');
```

## Find a folder by name
Provide only the folder name. A delimiter is not required.

```php
/** @var \Webklex\PHPIMAP\Client $client */
/** @var \Webklex\PHPIMAP\Folder $folder */

$folder = $client->getFolderByName('name');
```

## Find a folder by name or path
Provide either a folder name or path. A delimiter is not required but can be provided as well.

```php
/** @var \Webklex\PHPIMAP\Client $client */
/** @var \Webklex\PHPIMAP\Folder $folder */

$folder = $client->getFolder($folder = "INBOX.name", $delimiter = null);
$folder = $client->getFolder($folder = "name", $delimiter = null);
```

## Create new folder
Create a new folder. If you toggle expunge, your current imap session might not recognize the new folder.

```php
/** @var \Webklex\PHPIMAP\Client $client */
/** @var \Webklex\PHPIMAP\Folder $folder */

$folder = $client->createFolder($folder = 'INBOX.name', $expunge = true);
```

## Get folder detail
You can receive basic information about a given folder. These include the number of messages, the next uid and a list
off all available flags.

```php
/** @var \Webklex\PHPIMAP\Client $client */
/** @var array $info */

$info = $client->checkFolder($folder = 'INBOX.name');
```

Example result:

```
array:5 [
  "flags" => array:1 [
    0 => array:6 [
      0 => "\Answered"
      1 => "\Flagged"
      2 => "\Deleted"
      3 => "\Seen"
      4 => "\Draft"
    ]
  ]
  "exists" => "65"
  "recent" => "0"
  "uidvalidity" => 1488899637
  "uidnext" => 202
]
```
