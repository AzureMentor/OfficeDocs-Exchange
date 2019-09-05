---
localization_priority: Normal
description: The OAB virtual directory is the distribution for the OAB. By default, when Microsoft Exchange Server is installed, a new virtual directory named OAB is created in the default internal website in Internet Information Services (IIS). If you have client-side users that connect to Microsoft Outlook from outside your organization's firewall, you can add an external website. Alternatively, when you run the New-OABVirtualDirectory cmdlet in Exchange Online PowerShell, a new virtual directory named OAB is created in the default IIS website on the local Exchange server.
ms.topic: article
author: msdmaguire
ms.author: dmaguire
ms.assetid: 2c70e21f-2b12-414a-9e8c-65634a767c72
ms.date: 7/11/2018
ms.reviewer: 
title: Create an offline address book virtual directory
ms.collection: exchange-online
audience: ITPro
ms.service: exchange-online
manager: serdars
ROBOTS: NOINDEX, NOFOLLOW

---

# Create an offline address book virtual directory

The OAB virtual directory is the distribution for the OAB. By default, when Microsoft Exchange Server is installed, a new virtual directory named OAB is created in the default internal website in Internet Information Services (IIS). If you have client-side users that connect to Microsoft Outlook from outside your organization's firewall, you can add an external website. Alternatively, when you run the **New-OABVirtualDirectory** cmdlet in Exchange Online PowerShell, a new virtual directory named OAB is created in the default IIS website on the local Exchange server.

Creating an OAB virtual directory isn't a common task. Exchange allows for one OAB virtual directory named OAB, and you should create an OAB virtual directory only if there is a problem with the existing OAB virtual directory, and the previous OAB virtual directory was removed.

For additional management tasks related to OABs, see [Offline address book procedures](offline-address-book-procedures.md).

> [!IMPORTANT]
> Before you create an OAB virtual directory, make sure that your users are aware of the changes you are making. This procedure may interrupt the OAB downloading process for your users.

## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Offline address books" entry in the [Email Address and Address Book Permissions](https://technet.microsoft.com/library/1c1de09d-16ef-4424-9bfb-eb7edffbc8c2.aspx) topic.

- The local Exchange server must have the Client Access server role installed.

- A default IIS website must exist (for example, /w3svc/1/root).

- A virtual directory named OAB doesn't already exist.

- Although Web-based distribution is enabled by default and doesn't require further configuration, we recommend that you enable Secure Sockets Layer (SSL) for the OAB distribution point.

- You can't use the Exchange admin center (EAC) to perform this procedure. You must use Exchange Online PowerShell.

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts for the Exchange admin center](../../accessibility/keyboard-shortcuts-in-admin-center.md).

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542) or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## Use Exchange Online PowerShell to create an OAB virtual directory

To create an OAB virtual directory with all of the default settings, you can run the **New-OABVirtualDirectory** cmdlet without any parameters. Use the following procedure to create an OAB virtual directory with custom settings.

> [!NOTE]
> When creating an OAB virtual directory, we recommend that you have SSL enabled.

This example creates an OAB virtual directory on the Client Access server named CASServer01 that has SSL enabled and an external URL.

```
New-OABVirtualDirectory -Server CASServer01 -RequireSSL $true -ExternalURL "https://www.contoso.com/OAB"
```

After you create a new OAB virtual directory, you must edit the settings on each OAB that uses Web-based distribution to reconnect to the OAB virtual directory. For more information, see [Change the offline address book generation schedule](change-address-book-generation-schedule.md).

For detailed syntax and parameter information, see [New-OABVirtualDirectory](https://technet.microsoft.com/library/8f976c83-fd98-43c9-9d50-b252bdaae0fc.aspx).
