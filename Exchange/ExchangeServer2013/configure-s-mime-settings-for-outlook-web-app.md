---
title: 'Configure S/MIME settings in Exchange Server for Outlook Web App'
TOCTitle: Configure S/MIME settings for Outlook Web App
ms.assetid: c7dee22c-9b5b-425c-91a9-d093204ff84e
ms:mtpsurl:
ms:contentKeyID:
ms.date: 2/26/2019
ms.reviewer: 
manager: serdars
ms.author: dmaguire
author: msdmaguire
mtps_version: v=EXCHG.150
---

# Configure S/MIME settings in Exchange Server for Outlook on the web

_**Applies to:** Exchange Server 2013_

As an administrator for Exchange Server, you can set up Outlook on the web (formerly known as Outlook Web App) to allow sending and receiving S/MIME-protected messages. Use the **Get-SmimeConfig** and **Set-SmimeConfig** cmdlets to view and manage this feature in the Exchange Management Shell. To open the Exchange Management Shell, see [Open the Exchange Management Shell](https://docs.microsoft.com/powershell/exchange/exchange-server/open-the-exchange-management-shell).

For detailed syntax and parameter information, see [Get-SmimeConfig](http://technet.microsoft.com/library/4b29fa89-0840-4fe9-8885-019fcef2e02b.aspx) and [Set-SmimeConfig](http://technet.microsoft.com/library/de357ce0-8143-4c36-8032-026292fc63f0.aspx).

## Considerations for Chrome

To use S/MIME in Outlook on the web in the Google Chrome web browser, you (or another administrator) must set up and configure the Chromium policy named **ExtensionInstallForcelist** to install the Microsoft S/MIME extension in Chrome. The policy value is: `maafgiompdekodanheihhgilkjchcakm;https://<OWAUrl>/SmimeCrxUpdate.ashx` where \<OWAUrl\> is your URL value. For example: `maafgiompdekodanheihhgilkjchcakm;https://mail.contoso.com/owa/SmimeCrxUpdate.ashx`. And note that applying this policy requires domain-joined computers, so using S/MIME in Chrome effectively requires domain-joined computers.

For details about the **ExtensionInstallForcelist** policy, see [ExtensionInstallForcelist](http://dev.chromium.org/administrators/policy-list-3#ExtensionInstallForcelist).

This step is a prerequisite for using Chrome; it does not replace the S/MIME control that's installed by users. Users are prompted to download and install the S/MIME control in Outlook on the web during their first use of S/MIME. Or, users can proactively go to **S/MIME** in their Outlook on the web settings to get the download link for the control.

## For more information

[S/MIME for message signing and encryption](s-mime-for-message-signing-and-encryption.md)
