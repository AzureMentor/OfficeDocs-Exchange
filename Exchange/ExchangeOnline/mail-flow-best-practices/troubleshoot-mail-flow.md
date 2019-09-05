---
localization_priority: Normal
ms.author: dmaguire
manager: serdars
ms.topic: article
author: msdmaguire
ms.service: exchange-online
ms.assetid: ccb62ce1-a822-4859-a0db-3d546c5c1f50
ms.reviewer: 
ms.collection: 
- exchange-online
- M365-email-calendar
description: Admins can learn about the mail flow troubleshooting options in Office 365.
audience: ITPro
title: Troubleshoot Office 365 mail flow

---

# Troubleshoot Office 365 mail flow

Can't send or receive email? Office 365 for business has several ways that can troubleshoot the issue as an admin. We recommend using the automated solutions because they are typically easier and faster than manual troubleshooting.

For instructions about troubleshooting options, see [Find and fix email delivery issues as an Office 365 for business admin](../fix-outlook-connection-problems-in-office-365/fix-outlook-connection-problems-in-office-365/find-and-fix-email-delivery-issues-as-an-office-365-for-business-admin.md).

## Troubleshoot mail flow caused by connectors

To validate and troubleshoot mail flow from Office 365 to the email servers in your on-premises organization (also called the on-premises server), validate your connectors. You can set up and validate connectors on the **Connectors** page in the Exchange admin center (EAC). The built-in validation tests that your mail flow from Office 365 reaches:

- Your organization's email server

- A partner organization.

For more information, see [Validate connectors in Office 365](use-connectors-to-configure-mail-flow/validate-connectors.md).

## Troubleshoot mail flow issues caused by incorrect SPF records or MX records

 [Troubleshooting: Best practices for SPF in Office 365](https://technet.microsoft.com/library/3aff33c5-1416-4867-a23b-e0c0c5b4d2be.aspx#SPFTroubleshoot) gives tips on how to fix several SPF record errors. The beginning of that article also provides an explanation of what SPF records are and how Office 365 uses them to prevent spoofing.

Mail flow issues can also happen when your MX record is not setup correctly. To verify your MX record, see [Find and fix issues after adding your domain or DNS records in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=624017).

## For more information

[Mail flow best practices for Exchange Online and Office 365 (overview)](mail-flow-best-practices.md)

[Mail Flow in EOP](https://technet.microsoft.com/library/e109077e-cc85-4c19-ae40-d218ac7d0548.aspx)
