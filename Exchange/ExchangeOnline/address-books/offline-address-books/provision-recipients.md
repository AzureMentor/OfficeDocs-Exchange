---
localization_priority: Normal
description: Admins can learn how to assign offline address books (OABs) to mailboxes in Exchange Online.
ms.topic: article
author: msdmaguire
ms.author: dmaguire
ms.assetid: 141751ac-16d3-4e3c-b70c-004aeedcb5a0
ms.date: 
ms.reviewer: 
title: Provision recipients for offline address book downloads in Exchange Online
ms.collection: exchange-online
audience: ITPro
ms.service: exchange-online
manager: serdars

---

# Provision recipients for offline address book downloads in Exchange Online

If you use multiple offline address books (OABs) in your organization, you have different options for assigning the OAB to users:

- **Per mailbox**: You can use the **Set-Mailbox** cmdlet in Exchange Online PowerShell to assign the OAB to a mailbox. You can also assign the OAB to a filtered list of mailboxes.

- **Per address book policy**: You can assign an address book policy (ABP) to a user, and the ABP specifies the OAB. If you assign an ABP to a user that already has an OAB assigned to their mailbox, the OAB that's assigned to the mailbox will take precedence. For more information, see [Assign an address book policy to mail users](../../address-books/address-book-policies/assign-an-address-book-policy-to-mail-users.md).

For additional management tasks related to OABs, see [Offline address book procedures](offline-address-book-procedures.md).

## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Recipient Provisioning Permissions" section in the [Recipients permissions](https://technet.microsoft.com/library/5b690bcb-c6df-4511-90e1-08ca91f43b37.aspx) topic.

- You can't use the Exchange admin center (EAC) to perform this procedure. You can only use Exchange Online PowerShell. To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542) or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## Use Exchange Online PowerShell to assign OABs to mailboxes

To assign an OAB to a mailbox, use the following syntax:

```
Set-Mailbox -Identity <MailboxIdentity> -OfflineAddressBook <OfflineAddressBookIdentity>
```

This example assigns the OAB named Contoso Executives to the mailbox laura@contoso.com.

```
Set-Mailbox -Identity laura@contoso.com -OfflineAddressBook "Contoso Executives OAB"
```

This example assigns the OAB named Contoso US to a filtered list of mailboxes. This first command identifies the mailboxes. The second command assigns the OAB to the identified mailboxes.

```
$USContoso = Get-User -ResultSize Unlimited -Filter {RecipientType -eq "UserMailbox" -and Company -eq "Contoso" -and CountryOrRegion -eq "US"}
$USContoso | foreach {Set-Mailbox $_.Identity -OfflineAddressBook "Contoso United States"}
```

## How do you know this worked?

To verify that you've successfully assigned an OAB to a mailbox, replace <MailboxIdentity> with the identity of the mailbox, and run the following command:

```
Get-Mailbox -Identity "<MailboxIdentity>" | Format-Table Name,OfflineAddressBook -Auto
```
