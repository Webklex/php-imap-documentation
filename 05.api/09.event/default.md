---
title: Event
---

## Available events
The following events are available and used:

- `MessageNewEvent($message)` — can get triggered by `Folder::idle`
- `MessageDeletedEvent($message)` — triggered by `Message::delete`
- `MessageRestoredEvent($message)` — triggered by `Message::restore`
- `MessageMovedEvent($old_message, $new_message)` — triggered by `Message::move`
- `MessageCopiedEvent($old_message, $new_message)` — triggered by `Message::copy`
- `FlagNewEvent($flag)` — triggered by `Message::setFlag`
- `FlagDeletedEvent($flag)` — triggered by `Message::unsetFlag`
- `FolderNewEvent($folder)` — can get triggered by `Client::createFolder`
- `FolderDeletedEvent($folder)` — triggered by `Folder::delete`
- `FolderMovedEvent($old_folder, $new_folder)` — triggered by `Folder::move`


## Custom event
You can create and register your own events.

```php
class CustomMessageNewEvent extends Webklex\PHPIMAP\Events\MessageNewEvent {

    /**
     * Create a new event instance.
     * @var \Webklex\PHPIMAP\Message[] $messages
     * @return void
     */
    public function __construct($messages) {
        $this->message = $messages[0];
        echo "New message: ".$this->message->subject."\n";
    }
}
```

You can now either register it as default inside your [configuration](../../configuration/events) or inject it directly:

```php
/** @var \Webklex\PHPIMAP\Client $client */
/** @var \Webklex\PHPIMAP\Folder $folder */

$client->setEvent("message", "new", CustomMessageNewEvent::class);
$folder->setEvent("message", "new", CustomMessageNewEvent::class);
```
