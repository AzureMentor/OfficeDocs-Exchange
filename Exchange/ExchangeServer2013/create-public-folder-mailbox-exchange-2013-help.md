---
title: 'Create a public folder mailbox: Exchange 2013 Help'
TOCTitle: Create a public folder mailbox
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 
ms.reviewer: 
ms.assetid: 64437ffd-231b-4c10-84df-232ccbe9538f
mtps_version: v=EXCHG.150
---

# Create a public folder mailbox in Exchange 2013

_**Applies to:** Exchange Server 2013_

Before you can create a public folder, you must first create a public folder mailbox. Public folder mailboxes contain the hierarchy information plus the content for public folders. The first public folder mailbox you create will be the primary hierarchy mailbox, which contains the only writable copy of the hierarchy. Any additional public folder mailboxes you create will be secondary mailboxes, which contain a read-only copy of the hierarchy.

> [!NOTE]
> For more information about the storage quotas and limits for public folders, see [Limits for public folders](limits-for-public-folders-exchange-2013-help.md).

For additional management tasks related to public folders in Exchange 2013, see [Public Folder Procedures](http://technet.microsoft.com/library/afa54c8e-f3ab-4f5f-85ad-fb2a905ecfa9.aspx).

## What do you need to know before you begin?

- Estimated time to complete: less than 5 minutes.

- Exchange 2013 public folders and public folders on legacy Exchange servers can't exist in the same organization. If you try to create a public folder mailbox when you still have legacy public folders, you'll receive the error **An existing Public Folder deployment has been detected. To migrate existing Public Folder data, create new Public Folder mailbox using -HoldForMigration switch.**

  Before you can create public folders in Exchange 2013, you need to migrate your legacy public folders to Exchange 2013. To do this, follow the steps in [Migrate Public Folders to Exchange 2013 From Previous Versions](http://technet.microsoft.com/library/16773895-e9c3-4013-983f-683e5d14b221.aspx). These steps will show you how to create a public folder mailbox that can be used to store your migrated public folders.

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Public folders" entry in the [Sharing and collaboration permissions](http://technet.microsoft.com/library/b7fa4b7c-1266-45bd-a14b-f66be0459cc5.aspx) topic.

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts for the Exchange admin center in Exchange 2013](keyboard-shortcuts-in-the-exchange-admin-center-2013-help.md).

## Use the EAC to create a public folder mailbox

1. Navigate to **Public folders** \> **Public folder mailboxes**, and then click **Add** ![Add Icon](images/ITPro_EAC_AddIcon.gif).

2. In **Public Folder Mailbox**, provide a name for the public folder mailbox.

3. Click **Save**.

## Use the Shell to create a public folder mailbox

This example creates the primary public folder mailbox.

```powershell
New-Mailbox -PublicFolder -Name MasterHierarchy
```

This example creates a secondary public folder mailbox. The only difference between creating the primary hierarchy mailbox and a secondary hierarchy mailbox is that the primary mailbox is the first one created in the organization. You can create additional public folder mailboxes for load balancing purposes.

```powershell
New-Mailbox -PublicFolder -Name Istanbul
```

For detailed syntax and parameter information, see [New-Mailbox](http://technet.microsoft.com/library/42dbb25a-0b23-4775-ae15-7af62c089565.aspx).

## How do you know this worked?

To verify that you have successfully created the primary public folder mailbox, run the following Shell command:

```powershell
Get-OrganizationConfig | Format-List RootPublicFolderMailbox
```

For detailed syntax and parameter information, see [Get-OrganizationConfig](http://technet.microsoft.com/library/3e07e5cc-5066-40e7-8642-845ad080f9a9.aspx).

Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612).
