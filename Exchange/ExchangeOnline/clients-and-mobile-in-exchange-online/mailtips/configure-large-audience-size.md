---
localization_priority: Normal
description: You can use Exchange Online PowerShell to configure various settings that define how you use MailTips in your organization.
ms.topic: article
author: msdmaguire
ms.author: dmaguire
ms.assetid: 8a37911c-4339-4921-b5d3-0a5a774d4517
ms.date: 4/8/2015
ms.reviewer: 
title: Configure the large audience size for your organization
ms.collection: 
- exchange-online
- M365-email-calendar
audience: ITPro
ms.service: exchange-online
manager: serdars

---

# Configure the large audience size for your organization

You can use Exchange Online PowerShell to configure various settings that define how you use MailTips in your organization.

## What do you need to know before you begin?

- Estimated time to complete: 5 minutes

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "MailTips" entry in the [Mail flow permissions](https://technet.microsoft.com/library/f49f4fb5-af75-43cb-900f-c5f7b8cfa143.aspx) topic.

- You can only use Exchange Online PowerShell to perform this procedure.

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts for the Exchange admin center](../../accessibility/keyboard-shortcuts-in-admin-center.md).

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542) or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## Use Exchange Online PowerShell to configure the large audience size for your organization

You use the **Set-OrganizationConfig** cmdlet to configure the large audience size for your organization. When senders address messages to more recipients than the size you configure, they are shown the Large Audience MailTip. The large audience size is set to 25 by default. This example configures the large audience size to 50 in your organization.

```
Set-OrganizationConfig -MailTipsLargeAudienceThreshold 50
```

For detailed syntax and parameter information, see [set-OrganizationConfig](https://technet.microsoft.com/library/3b6df0fe-27c8-415f-ad0c-8b265f234c1a.aspx).
