---
localization_priority: Normal
description: Admins can learn how to view, create, modify, enable, disable, and delete journal rules in Exchange Online.
ms.topic: article
author: msdmaguire
ms.author: dmaguire
ms.assetid: d517f27e-f80a-4a06-988c-cbbf981c701d
ms.date: 
ms.reviewer: 
title: Manage journaling in Exchange Online
ms.collection: 
- exchange-online
- M365-email-calendar
audience: ITPro
ms.service: exchange-online
manager: serdars

---

# Manage journaling

Journaling can help your organization respond to legal, regulatory, and organizational compliance requirements by recording inbound and outbound email communications. For more information about journaling, see [Journaling in Exchange Online](journaling.md).

This topic shows you how to perform basic tasks related to managing journaling in Exchange Server and Exchange Online.

## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Journaling" entry in the [Messaging policy and compliance permissions](https://technet.microsoft.com/library/ec4d3b9f-b85a-4cb9-95f5-6fc149c3899b.aspx) topic.

- You need to have a journaling mailbox and (optionally) an alternate journaling mailbox configured. For more information, see [Configure Journaling in Exchange Online](configure-journaling.md).

- In Exchange Online, there's a limit to the number of journal rules that you can create. For details, see [Journal, Transport, and Inbox rule limits](https://docs.microsoft.com/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#journal-transport-and-inbox-rule-limits).

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts for the Exchange admin center](../../accessibility/keyboard-shortcuts-in-admin-center.md).

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542) or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351). If you're having trouble with the **JournalingReportDNRTo** mailbox, see [Transport and Mailbox Rules in Exchange Online don't work as expected](https://go.microsoft.com/fwlink/p/?LinkId=331674).

## Create a journal rule

### Use the EAC to create a journal rule

1. In the EAC, go to **Compliance management** \> **Journal rules**, and then click **Add** ![Add Icon](../../media/ITPro_EAC_AddIcon.gif).

2. In **Journal rule**, provide a name for the journal rule and then compete the following fields:

   - **If the message is sent to or received from**: Specify the recipient that the rule will target. You can either select a specific recipient or apply the rule to all messages.

   - **Journal the following messages**: Specify the scope of the journal rule. You can journal only the internal messages, only the external messages, or all messages regardless of origin or destination.

   - **Send journal reports to**: Type the address of the journaling mailbox that will receive all the journal reports.

   > [!NOTE]
   > You can also type the display name or alias of a mail user or a mail contact as the journal mailbox. In this case, journal reports will be sent to the external email address of the mail user or mail contact. But as previously explained, the external email address of a mail user or mail contact can't be the address of an Exchange Online mailbox.

3. Click **Save** to create the journal rule.

### Use Exchange Online PowerShell to create a journal rule

This example creates the journal rule Discovery Journal Recipients to journal all messages sent from and received by the recipient user1@contoso.com.

```
New-JournalRule -Name "Discovery Journal Recipients" -Recipient user1@contoso.com -JournalEmailAddress "Journal Mailbox" -Scope Global -Enabled $True
```

### How do you know this worked?

To verify that you have successfully created the journal rule, do one of the following:

- From the EAC, verify that the new journal rule you created is listed on the **Journal rules** tab.

- From Exchange Online PowerShell, verify that the new journal rule exists by running the following command (the example below verifies the rule created in Exchange Online PowerShell example above):

   ```
   Get-JournalRule -Identity "Discovery Journal Recipients"
   ```

## View or modify a journal rule

### Use the EAC to view or modify a journal rule

1. In the EAC, go to **Compliance management** \> **Journal rules**.

2. In the list view, you'll see all the journal rules in your organization.

3. Double-click the rule you want to view or modify.

4. In **Journal Rule**, modify the settings you want. For more information about the settings in this dialog box, see the procedure [Use the EAC to create a journal rule](#use-the-eac-to-create-a-journal-rule) earlier in this topic.

### Use Exchange Online PowerShell to view or modify a journal rule

This example displays a summary list of all journal rules in the Exchange organization:

```
Get-JournalRule
```

This example retrieves the journal rule Brokerage Journal Rule, and pipes the output to the **Format-List** command to display rule properties in a list format:

```
Get-JournalRule -Identity "Brokerage Journal Rule" | Format-List
```

If you want to modify the properties of a specific rule, you need to use the [Set-JournalRule](https://technet.microsoft.com/library/e72562c6-64d2-43c3-81b0-062e7d7b28c9.aspx) cmdlet. This example changes the name of the journal rule `JR-Sales` to `TraderVault`. The following rule settings are also changed:

- Recipient

- JournalEmailAddress

- Scope

```
Set-JournalRule -Identity "JR-Sales" -Name TraderVault -Recipient traders@woodgrovebank.com -JournalEmailAddress tradervault@woodgrovebank.com -Scope Internal
```

### How do you know this worked?

To verify that you have successfully modified a journal rule, do one of the following:

- From the EAC, go to **Compliance management**, \> **Journal rules**. Double-click the rule you modified and verify your changes were saved.

- From Exchange Online PowerShell, verify that you modified the journal rule successfully by running the following command. This command will list the properties you modified along with the name of the rule (the example below verifies the rule modified in Exchange Online PowerShell example above):

  ```
  Get-JournalRule -Identity "TraderVault" | Format-List Name,Recipient,JournalEmailAddress,Scope
  ```

## Enable or disable a journal rule

> [!IMPORTANT]
> When you disable a journal rule, the journaling agent will stop journaling messages targeted by that rule. While a journal rule is disabled, any messages that would have normally been journaled by the rule aren't journaled. Make sure that you don't compromise the regulatory or compliance requirements of your organization by disabling a journaling rule.

### Use the EAC to enable or disable a journal rule

1. In the EAC, go to **Compliance management** \> **Journal rules**.

2. In the list view, in the **On** column next to the rule's name, select the check box to enable the rule or clear it to disable the rule.

### Use Exchange Online PowerShell to enable or disable a journal rule

This example enables the rule Contoso.

```
Enable-JournalRule -Identity "Contoso Journal Rule"
```

This example disables the rule Contoso.

```
Disable-JournalRule -Identity "Contoso Journal Rule"
```

### How do you know this worked?

To verify that you have successfully enabled or disabled a journal rule, do one of the following:

- From the EAC, view the list of journal rules check the status of the check box in the **On** column.

- From Exchange Online PowerShell, run the following command to return a list of all journal rules in your organization along, including their status:

  ```
  Get-JournalRule | Format-Table Name,Enabled
  ```

## Remove a journal rule

### Use the EAC to remove a journal rule

1. In the EAC, go to **Compliance management** \> **Journal rules**.

2. In the list view, select the rule you want to remove, and then click **Delete** ![Delete icon](../../media/ITPro_EAC_DeleteIcon.gif).

### Use Exchange Online PowerShell to remove a journal rule

This example removes the rule Brokerage Journal Rule.

```
Remove-JournalRule -Identity "Brokerage Journal Rule"
```

### How do you know this worked?

To verify that you have successfully removed the journal rule, do one of the following:

- From the EAC, verify that the rule you removed is no longer listed on the **Journal rules** tab.

- From Exchange Online PowerShell, run the following command to verify that the rule you removed is no longer listed:

  ```
  Get-JournalRule
  ```

## For more information

[Disable or Enable Journaling of Voice Mail and Missed Call Notifications](https://technet.microsoft.com/library/5164a92e-69e6-4339-b80c-0cfbf0dc0198.aspx)

[New-JournalRule](https://technet.microsoft.com/library/fcad9ef1-b3f2-442d-a1a7-cd1bbe442054.aspx)

[Get-JournalRule](https://technet.microsoft.com/library/7620913f-cf28-4e82-983f-61a79f0b6e5a.aspx)

[Set-JournalRule](https://technet.microsoft.com/library/e72562c6-64d2-43c3-81b0-062e7d7b28c9.aspx)

[Enable-JournalRule](https://technet.microsoft.com/library/9a4b01b9-27d4-41e6-9573-86e27e82de2d.aspx)

[Disable-JournalRule](https://technet.microsoft.com/library/0324144b-2818-4e7f-a483-d6d6a19f8276.aspx)

[Remove-JournalRule](https://technet.microsoft.com/library/7cb9d691-2b0c-4f64-982d-ce69f3c3e757.aspx)
