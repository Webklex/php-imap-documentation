---
title: Getting started
---

This is a basic example, which will echo out all Mails within all folders and will move every message into
INBOX.read. Please be aware that this should not be tested in real life and is only meant to gives an impression on
how things work.

```php
use Webklex\PHPIMAP\ClientManager;
use Webklex\PHPIMAP\Client;

$cm = new ClientManager('path/to/config/imap.php');

// or use an array of options instead
$cm = new ClientManager($options = []);

/** @var \Webklex\PHPIMAP\Client $client */
$client = $cm->account('account_identifier');

// or create a new instance manually
$client = $cm->make([
    'host'          => 'somehost.com',
    'port'          => 993,
    'encryption'    => 'ssl',
    'validate_cert' => true,
    'username'      => 'username',
    'password'      => 'password',
    'protocol'      => 'imap'
]);

//Connect to the IMAP Server
$client->connect();

//Get all Mailboxes
/** @var \Webklex\PHPIMAP\Support\FolderCollection $folders */
$folders = $client->getFolders();

//Loop through every Mailbox
/** @var \Webklex\PHPIMAP\Folder $folder */
foreach($folders as $folder){

    //Get all Messages of the current Mailbox $folder
    /** @var \Webklex\PHPIMAP\Support\MessageCollection $messages */
    $messages = $folder->messages()->all()->get();

    /** @var \Webklex\PHPIMAP\Message $message */
    foreach($messages as $message){
        echo $message->getSubject().'<br />';
        echo 'Attachments: '.$message->getAttachments()->count().'<br />';
        echo $message->getHTMLBody();

        //Move the current Message to 'INBOX.read'
        if($message->move('INBOX.read') == true){
            echo 'Message has ben moved';
        }else{
            echo 'Message could not be moved';
        }
    }
}
```
