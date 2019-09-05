---
title: 'Assign an address book policy to mail users: Exchange 2013 Help'
TOCTitle: Assign an address book policy to mail users
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 
ms.reviewer: 
ms.assetid: bdfe6575-24c0-47d0-9cfb-ece910db248b
mtps_version: v=EXCHG.150
---

# Assign an address book policy to mail users in Exchange 2013

_**Applies to:** Exchange Server 2013_

After you create an address book policy (ABP), you must assign it to mailbox users. Users aren't assigned a default ABP when their user account is created. If you don't assign an ABP to a user, the global address list (GAL) for your entire organization will be accessible to the user through Outlook and Outlook Web App. To learn more, see [Address book policies](address-book-policies-exchange-2013-help.md).

Interested in scenarios that use this procedure? See [Scenario: Deploying Address Book Policies](http://technet.microsoft.com/library/6ac3c87d-161f-447b-afb2-149ae7e3f1dc.aspx).

## What do you need to know before you begin?

- Estimated time to complete: Less than 5 minutes.

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Address book policies" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic.

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts for the Exchange admin center in Exchange 2013](keyboard-shortcuts-in-the-exchange-admin-center-2013-help.md).

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612).

## Use the EAC to assign an ABP to a mailbox user

1. Navigate to **Recipients** \> **Mailboxes**.

2. In the list view, select the user that you want to assign the policy to, and then click **Edit** ![Edit icon](images/ITPro_EAC_EditIcon.gif).

3. Click **Mailbox features**.

4. In the **Address book policy** list, select the ABP that you want to apply to this user.

5. Click **Save**.

## Use the EAC to assign an ABP to multiple mailbox users

1. Navigate to **Recipients** \> **Mailboxes**.

2. In the list view use the Ctrl key to select multiple users.

3. In the details pane, click **More options**.

4. Under **Address Book Policy**, click **Update**.

5. In the **Select Address Book Policy** list, select the ABP that you want to apply to these users.

6. Click **Save**.

## Use the Shell to assign an ABP to mailbox users

This example assigns the ABP All Fabrikam to the existing mailbox user joe@fabrikam.com.

```powershell
Set-Mailbox -Identity joe@fabrikam.com -AddressBookPolicy "All Fabrikam"
```

This example assigns the ABP ABP_EngineeringDepartment to all mailbox users whose `CustomAttribute11` value contains "Engineering Department".

```powershell
Get-Mailbox -Filter {(CustomAttribute11 -like "Engineering Department")} | Set-Mailbox -AddressBookPolicy ABP_EngineeringDepartment
```

For detailed syntax and parameter information, see [Set-Mailbox](http://technet.microsoft.com/library/a0d413b9-d949-4df6-ba96-ac0906dedae2.aspx) and [Get-Mailbox](http://technet.microsoft.com/library/8a5a6eb9-4a75-47f9-ae3b-a3ba251cf9a8.aspx).
