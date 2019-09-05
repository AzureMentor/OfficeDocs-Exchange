---
localization_priority: Normal
description: Learn how to use Exchange Online PowerShell to change the deleted item retention period for Exchange Online mailboxes.
ms.topic: article
author: msdmaguire
ms.author: dmaguire
ms.assetid: ce17f1ec-b96c-4c9e-b20a-507fe0afc684
ms.date: 
ms.reviewer: 
title: Change how long permanently deleted items are kept for an Exchange Online mailbox
ms.collection: 
- exchange-online
- M365-email-calendar
audience: ITPro
ms.service: exchange-online
manager: serdars

---

# Change how long permanently deleted items are kept for an Exchange Online mailbox

If you've *permanently* deleted an item in Microsoft Outlook or Outlook on the web (formerly known as Outlook Web App), the item is moved to a folder ( **Recoverable Items** \> **Deletions**) and kept there for 14 days, by default. You can change how long items are kept, up to a maximum of 30 days.

> [!NOTE]
> You must use Exchange Online PowerShell to make the change. Unfortunately, you can't currently do this directly in the Outlook or Outlook on the web.

## What do you need to know before you begin?

- Estimated time to complete each procedure: 3 minutes.

- If you want to place a mailbox on [In-Place Hold and Litigation Hold](../../security-and-compliance/in-place-and-litigation-holds.md) so the retention limit is ignored, make sure the mailbox has an Exchange Online (Plan 2) user license.

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Recipient Provisioning Permissions" section in the [Mailbox Permissions](https://technet.microsoft.com/library/5b690bcb-c6df-4511-90e1-08ca91f43b37.aspx) topic.

- You can only use Exchange Online PowerShell to perform this procedure. To learn how to use Windows PowerShell to connect to Exchange Online, see [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts for the Exchange admin center](../../accessibility/keyboard-shortcuts-in-admin-center.md).

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542) or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## Change how long permanently deleted items are kept

In these examples, we increase the retention period to 30 days, the maximum for Exchange Online mailboxes. But you can set the number to whatever you like, up to that limit.

**Example 1:**: Set Emily Maier's mailbox to keep deleted items for 30 days. In Exchange Online PowerShell, run the following command.

```
Set-Mailbox -Identity "Emily Maier" -RetainDeletedItemsFor 30
```

**Example 2:**: Set all user mailboxes in the organization to keep deleted items for 30 days. In Exchange Online PowerShell, run the following command.

```
Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'UserMailbox')} | Set-Mailbox -RetainDeletedItemsFor 30
```

Need more details about using these commands? See Exchange Online PowerShell Help topic [Set-Mailbox](https://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx).

> [!TIP]
> Need to keep deleted items for longer than 30 days? To do this, place the mailbox on In-Place Hold or Litigation Hold. This works because when a mailbox is placed on hold, deleted items are kept and retention settings for deleted items are ignored. See [In-Place Hold and Litigation Hold](../../security-and-compliance/in-place-and-litigation-holds.md).

## Check to be sure the value is changed

To check for one mailbox, run the following command:

```
Get-Mailbox <Name> | Format-List RetainDeletedItemsFor
```

Or to check for all mailboxes, run the following command:

```
Get-Mailbox -ResultSize unlimited -Filter {(RecipientTypeDetails -eq 'UserMailbox')} | Format-List Name,RetainDeletedItemsFor
```

## More about deleted items and retention time

When a user permanently deletes a mailbox item (such as an email message, a contact, a calendar appointment, or a task) in Microsoft Outlook and Outlook on the web, the item is moved to the **Recoverable Items** folder, and into a subfolder named **Deletions**.

A mailbox item is deleted and moved to the **Recoverable Items** folder when a user does one of the following:

- Deletes an item from the Deleted Items folder

- Empties the Deleted Items folder

- Permanently deletes an item by selecting it and pressing **Shift+Delete**

 How long deleted items are kept in the **Deletions** folder depends on the deleted item retention period that is set for the mailbox. An Exchange Online mailbox keeps deleted items for 14 days, by default. Use Exchange Online PowerShell, as shown above, to change this setting, to increase the period up to a maximum of 30 days.

Users can recover, or purge, deleted items before the retention time for a deleted item expires. To do so, they use the **Recover Deleted Items** feature in Outlook or Outlook on the web. See the following topics for [Outlook](https://go.microsoft.com/fwlink/p/?linkId=198206) or for [Outlook on the web](https://go.microsoft.com/fwlink/p/?LinkId=524924).

Additional help:

- If a user purges a deleted item, you can recover it before the deleted item retention period expires. For details, see [Recover deleted messages in a user's mailbox](recover-deleted-messages.md).

- To learn more about deleted item retention, the Recoverable Items folder, In-Place Hold, and Litigation Hold, see [Understanding Recoverable Items](https://technet.microsoft.com/library/efc48fb4-2ed8-4d05-93af-f3505fbc389d.aspx).
