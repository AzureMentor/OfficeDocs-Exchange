---
localization_priority: Normal
description: Admins can learn how to create of global address lists (GALs) in Exchange Online.
ms.topic: article
author: msdmaguire
ms.author: dmaguire
ms.assetid: 59e4955a-8999-4d17-be9f-23a41a23b929
ms.date: 
ms.reviewer: 
title: Create a global address list in Exchange Online
ms.collection: 
- exchange-online
- M365-email-calendar
audience: ITPro
ms.service: exchange-online
manager: serdars

---

# Create a global address list in Exchange Online

The built-in global address list (GAL) that's automatically created by Exchange Online includes every mail-enabled object in the organization. You can create additional GALs to separate users by organization or location, but a user can only see and use one GAL. For more information about address lists, see [Address lists in Exchange Online](address-lists.md).

If your organization uses address book policies (ABPs), you'll need to create additional GALs. To learn more, see [Address book policies in Exchange Online](../../address-books/address-book-policies/address-book-policies.md).

For additional GAL management tasks, see [Address list procedures in Exchange Online](address-list-procedures.md).

## What do you need to know before you begin?

- Estimated time to complete each procedure: 5 minutes.

- By default, the Address List role isn't assigned to any role groups in Exchange Online. To use any cmdlets that require the Address List role, you need to add the role to a role group. For more information, see [Modify role groups](../../permissions-exo/role-groups.md#modify-role-groups).

- You can only use Exchange Online PowerShell to perform the procedures in this topic. To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).

- For details about recipient filters in the Exchange Online PowerShell, see [Recipient filters for address lists in Exchange Online PowerShell](use-recipient-filters-to-create-an-address-list.md).

> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542) or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## Use Exchange Online PowerShell to create global address lists

To create a GAL, use the following syntax:

```
New-GlobalAddressList -Name "<GAL Name>" [<Precanned recipient filter | Custom recipient filter>]
```

This example creates a GAL with a precanned recipient filter:

- **Name**: Contoso GAL

- **Precanned recipient filter**: All recipient types where the **Company** value is Contoso.

```
New-GlobalAddressList -Name "Contoso GAL" -IncludedRecipients AllRecipients -ConditionalCompany Contoso
```

This example creates a GAL with a custom recipient filter:

- **Name**: Agency A GAL

- **Custom recipient filter**: All recipient types where the CustomAttribute15 property contains the value AgencyA.

```
New-GlobalAddressList -Name "Agency A GAL" -RecipientFilter {CustomAttribute15 -like "*AgencyA*"}
```

For detailed syntax and parameter information, see [New-GlobalAddressList](http://technet.microsoft.com/library/9349a281-f92f-40f9-bf29-2a2e138c2783.aspx).

#### How do you know this worked?

To verify that you've successfully created a GAL, replace _\<GAL Name\>_ with the name of the GAL and run the following command in Exchange Online PowerShell to verify the property values:

```
Get-GlobalAddressList -Identity "<GAL Name>" | Format-List Name,RecipientFilterType,RecipientFilter,IncludedRecipients,Conditional*
```
