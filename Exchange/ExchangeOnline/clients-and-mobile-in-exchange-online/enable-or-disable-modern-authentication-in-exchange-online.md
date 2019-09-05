---
localization_priority: Priority
ms.topic: article
author: msdmaguire
ms.author: dmaguire
ms.assetid: 58018196-f918-49cd-8238-56f57f38d662
ms.reviewer: 
description: Admins can learn how to require Modern Auth or require Basic Auth for connections to Exchange Online by Outlook 2013 or later.
title: Enable modern authentication in Exchange Online
ms.collection:
- Adm_O365
- exchange-online
- M365-email-calendar
search.appverid:
- BCS160
- MOE150
- MED150
- MET150
audience: Admin
ms.custom:
- Adm_O365
- Adm_O365_FullSet
- MiniMaven
ms.service: exchange-online
manager: serdars

---

# Enable modern authentication in Exchange Online

Modern authentication in Exchange Online enables authentication features like multi-factor authentication (MFA) using smart cards, certificate-based authentication (CBA), and third-party SAML identity providers. Modern authentication is based on the [Active Directory Authentication Library](https://go.microsoft.com/fwlink/p/?LinkId=717281) (ADAL) and OAuth 2.0.

When you enable modern authentication in Exchange Online, Windows-based Outlook clients that support modern authentication (Outlook 2013 or later) use modern authentication to connect to Exchange Online mailboxes. For more information, see [How modern authentication works for Office client apps](https://support.office.com/article/e4c45989-4b1a-462e-a81b-2a13191cf517).

When you disable modern authentication in Exchange Online, Windows-based Outlook clients that support modern authentication use basic authentication to connect to Exchange Online mailboxes. They don't use modern authentication.

 **Notes**:

- Modern authentication is enabled by default in Exchange Online, Skype for Business Online and SharePoint Online.

- Enabling or disabling modern authentication in Exchange Online as described in this topic **only** affects modern authentication connections by Windows-based Outlook clients that support modern authentication (Outlook 2013 or later).

- Enabling or disabling modern authentication in Exchange Online as described in this topic **does not** affect other email clients that support modern authentication (for example, Outlook Mobile, Outlook for Mac 2016, and Exchange ActiveSync in iOS 11 or later). These other email clients **always** use modern authentication to log in to Exchange Online mailboxes.

- You should synchronize the state of modern authentication in Exchange Online with Skype for Business Online to prevent multiple log in prompts in Skype for Business clients. For instructions, see [Skype for Business Online: Enable your tenant for modern authentication](https://aka.ms/SkypeModernAuth).

- A user with multiple accounts configured in their Outlook profile might receive an error when they try to connect to their mailbox. For more information, see [KB 4516672](https://support.microsoft.com/en-us/help/4516672/outlook-shows-disconnected-after-enabling-modern-authentication-in-off)

## Enable or disable modern authentication in Exchange Online for client connections in Outlook 2013 or later

1. [Connect to Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkID=534121).

2. Do one of these steps:

   - Run the following command to enable modern authentication connections to Exchange Online by Outlook 2013 or later clients:

     ```
     Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
     ```

     Note that the previous command does not block or prevent Outlook 2013 or later clients from using basic authentication connections.

   - Run the following command to prevent modern authentication connections (force the use of basic authentication connections) to Exchange Online by Outlook 2013 or later clients:

     ```
     Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
     ```

3. To verify that the change was successful, run the following command:

     ```
     Get-OrganizationConfig | Format-Table Name,OAuth* -Auto
     ```

## See also

[Using Office 365 modern authentication with Office clients](https://support.office.com/article/776c0036-66fd-41cb-8928-5495c0f9168a)

[Set up multi-factor authentication for Office 365 users](https://docs.microsoft.com/office365/admin/security-and-compliance/set-up-multi-factor-authentication)
