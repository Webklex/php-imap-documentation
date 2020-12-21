---
title: Commands
---

Let's assume you want to run the imap idle process in the background of your server to automatically handle new
messages. The following examples will show two major ways to archive this:

## Event driven
Start by adding the following to your `app/Console/Kernel.php` file:
```php
/**
 * The Artisan commands provided by your application.
 *
 * @var array
 */
protected $commands = [
    \Webklex\IMAP\Commands\ImapIdleCommand::class,
];
```
Now register an event listener as described by [the laravel docs](https://laravel.com/docs/7.x/events#event-subscribers).
If you don't use the default account, or if you want to add some of your own magic, you'll need to create a
custom command (see next section).

Finally test the command by running:
```bash
php artisan imap:idle
```

## Custom Command
Create a new file like `app/Console/Commands/CustomImapIdleCommand.php` and add the following:
```php
<?php
namespace App\Console\Commands;

use Webklex\IMAP\Commands\ImapIdleCommand;
use Webklex\PHPIMAP\Message;

class CustomImapIdleCommand extends ImapIdleCommand {

    /**
     * The name and signature of the console command.
     *
     * @var string
     */
    protected $signature = 'custom_command';

    /**
     * Holds the account information
     *
     * @var string|array $account
     */
    protected $account = "default";

    /**
     * Callback used for the idle command and triggered for every new received message
     * @param Message $message
     */
    public function onNewMessage(Message $message){
        $this->info("New message received: ".$message->subject);
    }

}
```
..and add the following to your `app/Console/Kernel.php` file:
```php
/**
 * The Artisan commands provided by your application.
 *
 * @var array
 */
protected $commands = [
    \App\Console\Commands\CustomImapIdleCommand::class,
];
```

Finally test the command by running:
```bash
php artisan custom_command
```
