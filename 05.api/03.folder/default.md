---
title: Folder
---

## New search query
You can receive a new message search query by using one of the following methods. They all do the same - different names
are available as aliases. Pick the one you like.

```php
/** @var \Webklex\PHPIMAP\Folder $folder */
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */

$query = $folder->query();
$query = $folder->search();
$query = $folder->messages();
```


## Check if the folder has sub folder
You can check if the current folder has any sub folders or "children".

```php
/** @var \Webklex\PHPIMAP\Folder $folder */
/** @var boolean $status */

$status = $folder->hasChildren();
```


## Move a folder
You can move a folder from its current location to any other currently not occupied location. This action might not be
reversible!

```php
/** @var \Webklex\PHPIMAP\Folder $folder */
/** @var boolean $status */

$status = $folder->move($new_folder = "INBOX.othername");
$status = $folder->rename($new_folder = "INBOX.othername");
```


## Delete a folder
You can delete a folder from its current location. This action might not be reversible!

```php
/** @var \Webklex\PHPIMAP\Folder $folder */
/** @var boolean $status */

$status = $folder->delete();
```


## Idle connection
You can idle the connection and "listen" for new incoming messages.

```php
/** @var \Webklex\PHPIMAP\Folder $folder */

$folder->idle(function($message){
    echo "New message with the subject '".$message->subject."' received\n";
}, $timeout = 1200);
```

## Get folder detail
You can receive basic information about the current folder. These include the number of messages, the next uid and a list
off all available flags.

```php
/** @var \Webklex\PHPIMAP\Folder $folder */
/** @var array $info */

$info = $folder->examine();
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


## Folder overview
Get a quick overview of all messages in the current folder matching a given sequence. The default sequence "1:*" will
fetch all messages beginning by the first.

```php
/** @var \Webklex\PHPIMAP\Folder $folder */
/** @var array $overview */

$overview = $folder->overview($sequence = "1:*");
```

Example result:
```
array:65 [
  ...
  201 => array:27 [
    "from" => array:1 [ …1]
    "to" => array:1 [ …1]
    "cc" => array:2 [ …2]
    "reply_to" => array:1 [ …1]
    "sender" => array:1 [ …1]
    "subject" => "message subject"
    "message_id" => "3ff121ba-f40e-6df9-cdc2-379aee6b9e36@somehost.com"
    "date" => Carbon\Carbon {#842 …3}
    "return_path" => "<info@somehost.com>"
    "received" => array:16 [ …16]
    "x_virus_scanned" => "Debian amavisd-new at mx1.somehost.com"
    "x_spam_flag" => "NO"
    "x_spam_score" => "-2.9"
    "x_spam_level" => ""
    "x_spam_status" => "No, score=-2.9 required=6.31 tests=[ALL_TRUSTED=-1, BAYES_00=-1.9] autolearn=ham autolearn_force=no"
    "autocrypt" => array:43 [ …43]
    "user_agent" => "Mozilla/5.0 (X11; Linux x86_64; rv:68.0) Gecko/20100101 Thunderbird/68.10.0"
    "mime_version" => "1.0"
    "content_type" => "text/plain"
    "content_transfer_encoding" => "8bit"
    "content_language" => "en-GB"
    "toaddress" => "Someone Somewhere <test@somehost.com>"
    "fromaddress" => "Someone Somewhere <info@somehost.com>"
    "ccaddress" => "'Someone Somewhere' <thatmsg@somehost.com>, test@somehost.com"
    "reply_toaddress" => "Someone Somewhere <info@somehost.com>"
    "senderaddress" => "Someone Somewhere <info@somehost.com>"
    "charset" => "utf-8"
  ]
]
```
