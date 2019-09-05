---
title: 'Update offline address book: Exchange 2013 Help'
TOCTitle: Update offline address book
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 
ms.reviewer: 
ms.assetid: 448a207e-41b4-4cef-9fe9-a68b81e2ec4e
mtps_version: v=EXCHG.150
---

# Update offline address book in Exchange 2013

_**Applies to:** Exchange Server 2013_

After you create an OAB or modify OAB settings, the changes aren't available to users until the OAB generation (OABGen) process has completed.

For additional management tasks related to OABs, see [Offline address book procedures](offline-address-book-procedures-exchange-2013-help.md).

## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Offline address books" entry in the [Email Address and Address Book Permissions](http://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic.

- You can't use the Exchange admin center (EAC) to perform this procedure. You must use the Shell.

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts for the Exchange admin center in Exchange 2013](keyboard-shortcuts-in-the-exchange-admin-center-2013-help.md).

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612).

## Use the Shell to update an OAB

This example updates the OAB named My OAB.

```powershell
Update-OfflineAddressBook -Identity "My OAB"
```

For detailed syntax and parameter information, see [Update-OfflineAddressBook](http://technet.microsoft.com/library/08ee5bd7-1c23-492e-8952-d37b2a61c022.aspx).
