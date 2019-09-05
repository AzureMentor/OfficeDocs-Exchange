---
localization_priority: Normal
description: When you create a Unified Messaging (UM) dial plan, you can configure the primary and secondary ways that callers can search for names to locate a user when they call an Outlook Voice Access number or a UM auto attendant that's associated with the dial plan. Callers can use touchtone inputs to locate a UM-enabled user.
ms.topic: article
author: msdmaguire
ms.author: dmaguire
ms.assetid: 3d93a037-5820-41d3-9206-69f534414daf
ms.date: 11/17/2014
ms.reviewer: 
title: Configure the primary way for Outlook Voice Access users to search in Exchange Online
ms.collection: exchange-online
audience: ITPro
ms.service: exchange-online
manager: serdars

---

# Configure the primary way for Outlook Voice Access users to search in Exchange Online

When you create a Unified Messaging (UM) dial plan, you can configure the primary and secondary ways that callers can search for names to locate a user when they call an Outlook Voice Access number or a UM auto attendant that's associated with the dial plan. Callers can use touchtone inputs to locate a UM-enabled user.

> [!NOTE]
> **None** isn't an available option for the primary way callers can search for names. When **None** is selected for the secondary way they can search for names, only the primary way will be available to callers. If you configure both the primary and secondary ways that callers can search for names, they will be prompted for both ways.

For additional management tasks related to UM dial plans, see [UM Dial Plan Procedures](https://technet.microsoft.com/library/1bda77c8-c4e2-4ae0-a001-76ae029bf843.aspx).

## What do you need to know before you begin?

- Estimated time to complete: Less than 1 minute.

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging Permissions](https://technet.microsoft.com/library/d326c3bc-8f33-434a-bf02-a83cc26a5498.aspx) topic.

- Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](../../voice-mail-unified-messaging/connect-voice-mail-system/create-um-dial-plan.md).

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts for the Exchange admin center](../../accessibility/keyboard-shortcuts-in-admin-center.md).

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542) or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## Use the EAC to change the primary dial by name method

1. In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.

2. In the list view, select the UM dial plan you want to change, and then click **Edit** ![Edit icon](../../media/ITPro_EAC_EditIcon.gif).

3. On the **UM dial plan** page, click **Configure**.

4. In **Settings**, under **Primary way to search for names**, use the drop-down list to select the option you want:

   - **Last first** (default)

   - **First last**

   - **SMTP address**

5. Click **Save**.

## Use Exchange Online PowerShell to change the primary dial by name method

This example sets the primary dial by name method to `FirstLast`. This enables callers who call the Outlook Voice Access number or a UM auto attendant associated with the dial plan to search for a UM-enabled user by their first and then last name.

```
Set-UMDialPlan -Identity MyUMDialPlan -DialByNamePrimary FirstLast
```

This example sets the primary dial by name method to `LastFirst`. This enables callers who call the Outlook Voice Access number or a UM auto attendant associated with the dial plan to search for a UM-enabled user by their last and then first name.

```
Set-UMDialPlan -Identity MyUMDialPlan -DialByNamePrimary LastFirst
```

This example sets the primary dial by name method to `SMTP address`. This enables callers who call the Outlook Voice Access number or a UM auto attendant associated with the dial plan to search for a UM-enabled user by their SMTP address.

```
Set-UMDialPlan -Identity MyUMDialPlan -DialByNamePrimary SMTPAddress
```
