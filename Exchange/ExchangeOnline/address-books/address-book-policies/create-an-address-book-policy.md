---
localization_priority: Normal
description: Learn how to create address book policies (ABPs) in Exchange Online.
ms.topic: article
author: msdmaguire
ms.author: dmaguire
ms.assetid: 6359abaf-e6f6-4667-8c2b-3860728b39a9
ms.date: 
ms.reviewer: 
title: Create an address book policy in Exchange Online
ms.collection: 
- exchange-online
- M365-email-calendar
audience: ITPro
ms.service: exchange-online
manager: serdars

---

# Create an address book policy in Exchange Online

Address book policies (ABPs) allow you to segment users into specific groups to give them customized global address lists (GALs) in Outlook and Outlook on the web (formerly known as Outlook Web App). For more information about ABPs, see [Address book policies in Exchange Online](address-book-policies.md).

In Exchange Online, you can only create ABPs in Exchange Online PowerShell.

An ABP requires one global address list (GAL), one offline address book (OAB), one room list, and one or more address lists. To view the available objects, use the **Get-GlobalAddressList**, **Get-OfflineAddressBook**, and **Get-AddressList** cmdlets.

  **Note**: The room list that's required for an ABP is an address list that specifies rooms (contains the filter `RecipientDisplayType -eq 'ConferenceRoomMailbox'`). It's not a room finder distribution group that you create with the _RoomList_ switch on the **New-DistributionGroup** or **Set-DistributionGroup** cmdlets.

## What do you need to know before you begin?

- Estimated time to complete: Less than 5 minutes.

- By default, the Address List role isn't assigned to any role groups in Exchange Online. To use any cmdlets or features that require the Address List role, you need to add the role to a role group. For more information, see [Modify role groups](../../permissions-exo/role-groups.md#modify-role-groups).

- To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).

- Creating an ABP for an organization is a multi-step process that requires planning. For more information, see [Scenario: Deploying Address Book Policies](https://technet.microsoft.com/library/6ac3c87d-161f-447b-afb2-149ae7e3f1dc.aspx).

- Having problems? Ask for help in the Exchange forums. Visit the forums at [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542) or [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## Use Exchange Online PowerShell to create an ABP

To create an ABP, use this syntax:

```
New-AddressBookPolicy -Name "<Unique Name>" -GlobalAddressList "<GAL>" -OfflineAddressBook "<OAB>" -RoomList "<RoomList>" -AddressLists "<AddressList1>","<AddressList2>"...
```

This example creates an ABP with the following settings:

- **Name**: All Fabrikam ABP

- **GAL**: All Fabrikam

- **OAB**: Fabrikam-All-OAB

- **Room list**: All Fabrikam Rooms

- **Address lists**: All Fabrikam, All Fabrikam Mailboxes, All Fabrikam DLs, and All Fabrikam Contacts

```
New-AddressBookPolicy -Name "All Fabrikam ABP" -AddressLists "\All Fabrikam","\All Fabrikam Mailboxes","\All Fabrikam DLs","\All Fabrikam Contacts" -OfflineAddressBook \Fabrikam-All-OAB -GlobalAddressList "\All Fabrikam" -RoomList "\All Fabrikam Rooms"
```

For detailed syntax and parameter information, see [New-AddressBookPolicy](https://technet.microsoft.com/library/07133bd2-ed6d-4a4b-8c3a-bd0c016f68eb.aspx).

### How do you know this worked?

To verify that you've successfully created an ABP, use either of these procedures in Exchange Online PowerShell:

- Run the following command to verify that the ABP is listed:

   ```
   Get-AddressBookPolicy
   ```

- Replace _\<ABPName\>_ with the name of the ABP, and run the following command to verify the property values:

   ```
   Get-AddressBookPolicy -Identity "<ABPName>" | Format-List
   ```

## For more information

After you create an ABP, you need to assign the ABP to users. For instructions, see [Assign an address book policy to users in Exchange Online](assign-an-address-book-policy-to-mail-users.md).
