---
title: 'Configure the number of input failures before Outlook Voice Access users are disconnected: Exchange 2013 Help'
TOCTitle: Configure the number of input failures before Outlook Voice Access users are disconnected
ms.author: dmaguire
author: msdmaguire
manager: serdars
ms.date: 11/17/2014
ms.reviewer: 
ms.assetid: 64c13d17-a26a-4c9b-b495-bd69c716456a
mtps_version: v=EXCHG.150
---

# Configure the number of input failures before Outlook Voice Access users are disconnected in Exchange Server

_**Applies to:** Exchange Server 2013, Exchange Server 2016_

You can configure the number of times that users who call in to an Outlook Voice Access number can enter incorrect data before they're disconnected. This setting applies to both Outlook Voice Access users and unauthenticated callers who use directory search.

The following are examples of types of data that are considered incorrect:

- A caller requests an extension number that isn't found in the system.

- The system can't locate the user's extension number to transfer the call.

- A caller presses a menu option that isn't valid.

The value of this setting can be from 1 through 20. For most organizations, this value should be set to the default of three attempts. Setting this value too low may prematurely disconnect callers.

For additional management tasks related to UM dial plans, see [UM Dial Plan Procedures](http://technet.microsoft.com/library/1bda77c8-c4e2-4ae0-a001-76ae029bf843.aspx).

## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging Permissions](http://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic.

- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](create-um-dial-plan-exchange-2013-help.md).

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts for the Exchange admin center in Exchange 2013](keyboard-shortcuts-in-the-exchange-admin-center-2013-help.md).

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Server](https://go.microsoft.com/fwlink/p/?linkId=60612).

## Use the EAC to configure the input failures before disconnect

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.

2. In the list view, select the UM dial plan you want to modify, and then click **Edit** ![Edit icon](images/ITPro_EAC_EditIcon.gif).

3. On the **UM dial plan** page, click **Configure**.

4. In **Settings**, under **Number of input failures before disconnecting**, enter the number of input failures.

5. Click **Save**.

## Use the Shell to configure the input failures before disconnect

This example sets the input failures before disconnect to 5 on a UM dial plan named `MyUMDialPlan`.

```powershell
Set-UMDialPlan -identity MyUMDialPlan -InputFailuresBeforeDisconnect 5
```