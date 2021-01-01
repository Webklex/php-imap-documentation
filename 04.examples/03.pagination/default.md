---
title: Message pagination
---

Assuming you obtained a new query instance and which to paginate the result.

```php
/** @var \Webklex\PHPIMAP\Support\MessageCollection $messages */
/** @var \Illuminate\Pagination\LengthAwarePaginator $paginator */

/** @var integer $per_page Results you which to receive per page */
/** @var integer $page The current page you are on (e.g. 0, 1, 2, ...) use `null` to enable auto mode */
/** @var string $page_name The page name / uri parameter used for the generated links and the auto mode */

$paginator = $messages->paginate($per_page = 5, $page = null, $page_name = 'imap_page');
```

HTML view example:

```
<table>
    <thead>
    <tr>
        <th>UID</th>
        <th>Subject</th>
        <th>From</th>
        <th>Attachments</th>
    </tr>
    </thead>
    <tbody>
        <?php if($paginator->count() > 0): ?>
            <?php foreach($paginator as $message): ?>
            <tr>
                <td><?php echo $message->getUid(); ?></td>
                <td><?php echo $message->getSubject(); ?></td>
                <td><?php echo $message->getFrom()[0]->mail; ?></td>
                <td><?php echo $message->getAttachments()->count() > 0 ? 'yes' : 'no'; ?></td>
            </tr>
            <?php endforeach; ?>
        <?php else: ?>
            <tr>
                <td colspan="4">No messages found</td>
            </tr>
        <?php endif; ?>
    </tbody>
</table>

<?php echo $paginator->links(); ?>
```

You can also paginate folder, attachment or flag collections:

```php
/** @var \Webklex\PHPIMAP\Support\FolderCollection $folders */
/** @var \Webklex\PHPIMAP\Support\AttachmentCollection $attachments */
/** @var \Webklex\PHPIMAP\Support\FlagCollection $flags */
/** @var \Illuminate\Pagination\LengthAwarePaginator $paginator */

$paginator = $folders->paginate($per_page = 5, $page = null, $page_name = 'imap_page');
$paginator = $attachments->paginate($per_page = 5, $page = null, $page_name = 'imap_page');
$paginator = $flags->paginate($per_page = 5, $page = null, $page_name = 'imap_page');
```
