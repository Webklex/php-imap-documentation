---
title: Events
---

The following events are available:
- `Webklex\IMAP\Events\MessageNewEvent($message)` &mdash; can get triggered by `Folder::idle`
- `Webklex\IMAP\Events\MessageDeletedEvent($message)` &mdash; triggered by `Message::delete`
- `Webklex\IMAP\Events\MessageRestoredEvent($message)` &mdash; triggered by `Message::restore`
- `Webklex\IMAP\Events\MessageMovedEvent($old_message, $new_message)` &mdash; triggered by `Message::move`
- `Webklex\IMAP\Events\MessageCopiedEvent($old_message, $new_message)` &mdash; triggered by `Message::copy`
- `Webklex\IMAP\Events\FlagNewEvent($flag)` &mdash; triggered by `Message::setFlag`
- `Webklex\IMAP\Events\FlagDeletedEvent($flag)` &mdash; triggered by `Message::unsetFlag`
- `Webklex\IMAP\Events\FolderNewEvent($folder)` &mdash; can get triggered by `Client::createFolder`
- `Webklex\IMAP\Events\FolderDeletedEvent($folder)` &mdash; triggered by `Folder::delete`
- `Webklex\IMAP\Events\FolderMovedEvent($old_folder, $new_folder)` &mdash; triggered by `Folder::move`

Additional integration information:
- [Generic event integration](../../../api/event)
- [laravel.com/docs/7.x/events#event-subscribers](https://laravel.com/docs/7.x/events#event-subscribers)
- [laravel.com/docs/5.2/events#event-subscribers](https://laravel.com/docs/5.2/events#event-subscribers)
- [github.com/Webklex/php-imap#events](https://github.com/Webklex/php-imap#events)
