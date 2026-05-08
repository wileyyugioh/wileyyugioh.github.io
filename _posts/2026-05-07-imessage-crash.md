---
title: Fixing iMessage CPU Hang from Corrupted Attachment
tags: info
---

Recently, I got sent a sticker on iMessage that could be seen on my iPhone, but whenever it tried to load on my Mac, it would cause the CPU usage to spike to >100% and caused general sluggishness. Restarting and turning on and off contact syncing did not help. I managed to identify the problem by noticing that the issue would only occur when the message thread for that particular contact was loaded and the sticker would not appear in the message thread. I didn't want to delete all my messages, so I managed to solve the issue my modifying the SQL database, and will record the steps and logic chain here.


Change directory, make a backup, and open the database.

```
cd ~/Library/Messages
cp chat.db chat.db.bak
sqlite3 chat.db
```


First thing I had to do was find the contact handle for the person who sent the corrupted attachment.

```
SELECT ROWID, id FROM handle WHERE id LIKE '+1234567890';
```

where "+1234567890" is the person's phone number. Another potential id could be their email/Apple ID. For me, this spat out two handles with identical phone numbers.

```
309|+1234567890
315|+1234567890
```

Then, I wanted to see what the most recent messages were.

```
SELECT ROWID, text, date FROM message WHERE handle_id = 309 ORDER BY date DESC LIMIT 10;
```

When I first tried the `handle_id` 309, it gave me messages that were way too old. `handle_id` 315 gave me my most recent messages. If the corrupting message is not there, you may need to increase the `LIMIT` to a larger number. For me, the corrupted message had no text, but I could identify it by looking at the order of the messages sent on my iPhone and finding the row that was in the correct place since they are sorted by time. It looked something like

```
308435||799895917811926656
```

At first, I tried deleting the message 308435, but kept getting a parse error.

```
sqlite> DELETE FROM message WHERE ROWID = 308435;
Parse error: no such function: after_delete_message_plugin
```

Searching online was no help. Instead, I just overwrote the data and flagged it as deleted.

```
UPDATE message
SET text = '[deleted]',
    attributedBody = NULL -- removes any rich text / formatting
WHERE ROWID = 308435;
```

You may need to restart your computer. Afterwards, my Messages app was back to normal and not laggy anymore. Cool!
