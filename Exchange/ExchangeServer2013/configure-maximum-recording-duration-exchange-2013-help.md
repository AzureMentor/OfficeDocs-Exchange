---
title: 'Configure the maximum recording duration: Exchange 2013 Help'
TOCTitle: Configure the maximum recording duration
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 11/17/2014
ms.reviewer: 
ms.assetid: 18eeb567-1048-4c82-93cf-612cb12ec5e3
mtps_version: v=EXCHG.150
---

# Configure the maximum recording duration in Exchange Server

_**Applies to:** Exchange Server 2013, Exchange Server 2016_

You can specify the maximum number of minutes allowed for each voice recording when a caller leaves a voice mail message. This value can be set to a number from 1 through 100. For most organizations, this value should be set to the default of 20 minutes. Setting this value too low can cause long voice messages to be disconnected before they're completed. Setting this value too high lets users save lengthy voice messages in their Inboxes.

This setting is important if you've implemented strict disk quotas for users. It must be set to a lower value than the one set for **Maximum call duration (minutes)**.

For additional tasks related to UM dial plans, see [UM Dial Plan Procedures](http://technet.microsoft.com/library/1bda77c8-c4e2-4ae0-a001-76ae029bf843.aspx).

## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic.

- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](create-um-dial-plan-exchange-2013-help.md).

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts for the Exchange admin center in Exchange 2013](keyboard-shortcuts-in-the-exchange-admin-center-2013-help.md).

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612).

## Use the EAC to configure the maximum recording duration

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.

2. In the list view, select the UM dial plan you want to modify, and then click **Edit** ![Edit icon](images/ITPro_EAC_EditIcon.gif).

3. On the **UM dial plan** page, click **Configure**.

4. In **Settings**, under **Maximum recording duration (minutes)**, enter the number in minutes.

5. Click **Save**.

## Use the Shell to configure the maximum recording duration

This example sets the maximum recording duration to 10 minutes for a UM dial plan named `MyUMDialPlan`.

```powershell
Set-UMDialPlan -identity MyUMDialPlan -MaxRecordingDuration 10
```
