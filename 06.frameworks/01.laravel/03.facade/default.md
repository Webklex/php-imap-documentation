---
title: Facade
---

If you use the Facade, please start by selecting an in config/imap.php defined account first, followed by
`Client::connect()` to establish an authenticated connection.

```php
use Webklex\IMAP\Facades\Client;

/** @var \Webklex\PHPIMAP\Client $client */
$client = Client::account('default');
$client->connect();
```

The facade is an initialized alias for the [ClientManager](../../../api/client-manager) class and therefor has the same
functionality.
