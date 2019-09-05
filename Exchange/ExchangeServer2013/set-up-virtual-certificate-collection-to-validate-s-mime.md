---
title: 'Set up a virtual certificate collection in Exchange Server to validate S/MIME'
TOCTitle: Send and receive S/MIME signed and encrypted email
ms.assetid: 04a616e6-197c-490c-ae8c-c8d5f0f0b3dd
ms:mtpsurl:
ms:contentKeyID:
ms.date: 2/26/2019
ms.reviewer: 
manager: serdars
ms.author: dmaguire
author: msdmaguire
mtps_version: v=EXCHG.150
---

# Set up a virtual certificate collection in Exchange Server to validate S/MIME

_**Applies to:** Exchange Server 2013_

As an Exchange Server administrator, you need to configure a virtual certificate collection in Exchange that will be used to validate S/MIME certificates. This virtual certificate collection is set up as a certificate store with an SST filename extension. The SST file contains all the root and intermediate certificates that are used when validating an S/MIME certificate.

## Create and save an SST

You can create this SST certificate store file by exporting the certificates from a trusted machine using the **Export-Certificate** cmdlet in Windows PowerShell and specifying the _Type_ value as SST. For instructions, see [Export-Certificate](https://docs.microsoft.com/powershell/module/pkiclient/export-certificate).

Once you have the SST certificate store file, use the following syntax in the Exchange Management Shell to save the SST file contents in the Exchange Online virtual certificate store. To open the Exchange Management Shell, see [Open the Exchange Management Shell](https://docs.microsoft.com/powershell/exchange/exchange-server/open-the-exchange-management-shell).

```
Set-SmimeConfig -SMIMECertificateIssuingCA (Get-Content <FileNameAndPath>.sst -Encoding Byte)
```

This example imports the SST file C:\My Documents\Exported Certificate Store.sst.

```
Set-SmimeConfig -SMIMECertificateIssuingCA (Get-Content "C:\My Documents\Exported Certificate Store.sst" -Encoding Byte)
```

For detailed syntax and parameter information, see [Set-SmimeConfig](https://docs.microsoft.com/en-us/powershell/module/exchange/encryption-and-certificates/set-smimeconfig).

## Validating certificates

Exchange 2013 SP1 or later first checks for the SST file and validates the certificate. If the validation fails, it will look at the local machine certificate store to validate the certificate. This behavior is different from previous versions of Exchange.

## More Information

[S/MIME for message signing and encryption](s-mime-for-message-signing-and-encryption.md)

[Get-SmimeConfig](http://technet.microsoft.com/library/4b29fa89-0840-4fe9-8885-019fcef2e02b.aspx)
