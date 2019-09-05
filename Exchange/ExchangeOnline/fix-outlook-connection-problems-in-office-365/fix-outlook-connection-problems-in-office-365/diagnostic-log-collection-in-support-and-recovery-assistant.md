---
localization_priority: Normal
description: 'Learn about diagnostic log collection in Support and Recovery Assistant for Office 365. '
ms.topic: article
author: msdmaguire
ms.author: dmaguire
ms.assetid: 5f76de29-9ee3-47de-84ce-2d49fdc32174
ms.reviewer: 
title: Turn off diagnostic log collection in Support and Recovery Assistant for Office 365
ms.collection: 
- exchange-online
- M365-email-calendar
search.appverid:
- BCS160
- MET150
- MOE150
audience: Admin
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
ms.service: exchange-online
manager: serdars

---

# Turn off diagnostic log collection in Support and Recovery Assistant for Office 365

By default, [Support and Recovery Assistant for Office 365](https://diagnostics.office.com) collects diagnostic logs to help troubleshoot problems in the following scenarios:

- Support and Recovery Assistant sometimes collects diagnostic logs when the tool fails to solve a user's problem.

- Support and Recovery Assistant collects diagnostic logs when a user chooses to run advanced diagnostics. Typically this happens at the request of an admin or Microsoft support engineer.

   ![Screenshot of Support and Recovery Assistant scenario selection screen with Advanced diagnostics selected.](../../media/daa5ca72-85b3-42c5-8837-18e246e3b7c6.png)

Office 365 uses diagnostic logs to improve the tool to provide better troubleshooting in the future. Microsoft support engineers can also use these logs to analyze your user's specific issue more throughly. As an admin, you can make a registry edit to prevent users from collecting diagnostic logs if your organization wants to limit data sharing.

> [!CAUTION]
> Registry Editor is a tool intended for advanced users. Follow the steps in this article carefully to make sure you only make changes to data collection for Support and Recovery Assistant. Before making changes to the registry, create a backup in case something goes wrong. For more information about creating a backup, see [How to back up and restore the registry in Windows](https://support.microsoft.com/kb/322756).

## Option 1: Create a new registry entry

To turn off data collection in Support and Recovery Assistant:

1. Copy and paste the following text into Notepad:

   ```
   Windows Registry Editor Version 5.00

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Support and Recovery Assistant]
   "UploadDiagnosticLogsDisabled"=dword:00000001
   ```

2. Save the file with a .reg extension (instead of .txt).

3. Open File Explorer (formerly known as Windows Explorer), browse to the .reg file, and double-click on the file to add it to the registry.

For details about creating registry entries, see [How to add, modify, or delete registry subkeys and values by using a .reg file](https://support.microsoft.com/help/310516/how-to-add-modify-or-delete-registry-subkeys-and-values-by-using-a-reg).

With the registry entry in place, Support and Recovery Assistant can't collect diagnostic logs. If you want to re-enable log collection later, you can either change the value to 0 or delete the registry entry.

## Option 2: Edit the existing registry entry

If you previously created a registry entry for Support and Recovery Assistant, you can edit the entry to turn off (or turn on) data collection.

1. Open Registry Editor (for example, run regedit.exe).

2. Go to the following registry location:

   `HKEY_LOCAL_MACHINE\Software\Microsoft\Support and Recovery Assistant`

3. Double-click the `UploadDiagnosticLogsDisabled` entry.

   **Note**: If you don't see `UploadDiagnosticLogsDisabled` in that registry location, you need to add it using the instructions in [Option 1: Create a new registry entry](#option-1-create-a-new-registry-entry).

4. In the **Edit DWORD (32-bit) Value** dialog box that opens, configure one of the following values for the **Value data** field:

   - **1**: Disable diagnostic log collection.

   - **0**: Enable diagnostic log collection.

5. When you're finished, click **OK** and close Registry Editor.

## Determine if Support and Recovery Assistant is collecting data

Support and Recovery Assistant will collect log data if either of the following statements are true:

- The `UploadDiagnosticLogsDisabled` value is not 1 (for example, 0).

- The `HKEY_LOCAL_MACHINE\Software\Microsoft\Support and Recovery Assistant` key does not exist.

## Related articles

- [Fix Outlook and Office 365 issues with Microsoft Support and Recovery Assistant for Office 365](fix-outlook-and-office-365-issues.md)

- [Microsoft Support and Recovery Assistant](https://diagnostics.outlook.com/)
