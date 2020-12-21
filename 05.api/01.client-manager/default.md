---
title: ClientManager
---
The `ClientManager` class can be used to establish and manage new client connections and provides the package configuration.

## New instance from config file
Provide the path of your configuration file as described in the [configuration](../../configuration/configuration) section.

```php
use Webklex\PHPIMAP\ClientManager;

$cm = new ClientManager('path/to/config/imap.php');
```

## New instance from array
Provide a config array based on the package [configuration](../../configuration/configuration) if you don't want to use
your own configuration.

```php
use Webklex\PHPIMAP\ClientManager;

$cm = new ClientManager($options = []);
```


## New preconfigured account
You can receive a client instance based on your preconfigured [available accounts](../../configuration/configuration).

```php
/** @var \Webklex\PHPIMAP\ClientManager $cm */
/** @var \Webklex\PHPIMAP\Client $client */

$client = $cm->account('account_identifier');
```


## Make a new client
If you haven't preconfigured the account, you can make a new client instance by providing the required
[account configuration](../../configuration/account/account).

```php
/** @var \Webklex\PHPIMAP\ClientManager $cm */
/** @var \Webklex\PHPIMAP\Client $client */

$client = $cm->make([
    'host'          => 'somehost.com',
    'port'          => 993,
    'encryption'    => 'ssl',
    'validate_cert' => true,
    'username'      => 'username',
    'password'      => 'password',
    'protocol'      => 'imap'
]);
```


## Get a specific config value
You can receive any config parameter by providing the a dotted key path.

```php
use Webklex\PHPIMAP\ClientManager;

$value = ClientManager::get('options.delimiter');
```
