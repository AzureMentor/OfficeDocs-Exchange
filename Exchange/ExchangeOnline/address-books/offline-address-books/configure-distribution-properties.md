---
localization_priority: Normal
description: 
ms.topic: article
author: msdmaguire
f1_keywords:
- Microsoft.Exchange.Management.SnapIn.Esm.Servers.ClientAccess.OabDistributionGeneralPage
ms.author: dmaguire
ms.assetid: 8df985e9-75ba-47ea-9cc3-aa98a5d8acf4
ms.date: 11/17/2014
ms.reviewer: 
title: Configure offline address book distribution properties
ms.collection: exchange-online
audience: ITPro
ms.service: exchange-online
manager: serdars
ROBOTS: NOINDEX, NOFOLLOW

---

# Configure offline address book distribution properties

For each offline address book (OAB) distribution point in Exchange, you can configure two URLs: an internal URL that can be accessed only from your internal corporate network and an external URL that can be accessed from the internet.

For additional management tasks related to OABs, see [Offline address book procedures](offline-address-book-procedures.md).

## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Offline address books" entry in the [Email Address and Address Book Permissions](https://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic.

- You can't use the Exchange admin center (EAC) to perform this procedure. You must use Exchange Online PowerShell.

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts for the Exchange admin center](../../accessibility/keyboard-shortcuts-in-admin-center.md).

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542) or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## Use Exchange Online PowerShell to configure OAB distribution properties

This example sets the polling interval for OAB distribution on the OAB virtual directory OAB (Default Web Site) to six hours.

```
Set-OABVirtualDirectory "OAB (Default Web Site)" -PollInterval 360
```

This example sets the external distribution point to https://contoso.com/OAB for the default OAB virtual directory OAB (Default Web Site).

```
Set-OABVirtualDirectory "OAB (Default Web Site)" -ExternalUrl https://contoso.com/OAB
```

For detailed syntax and parameter information, see [set-OabVirtualDirectory](https://technet.microsoft.com/library/d1184716-920c-47cf-9e03-638434c16462.aspx).

## For More Information

[Understanding Offline Address Books](https://technet.microsoft.com/library/a6bcb072-4ab9-400e-a5d0-c05264629097.aspx)
