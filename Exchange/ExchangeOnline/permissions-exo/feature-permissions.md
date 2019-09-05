---
localization_priority: Normal
description: The permissions required to perform tasks to manage Microsoft Exchange Online vary depending on the procedure being performed or the cmdlet you want to run.
ms.topic: article
author: msdmaguire
ms.author: dmaguire
ms.assetid: 15073ce1-0917-403b-8839-02a2ebc96e16
ms.date: 
ms.reviewer: 
title: Feature permissions in Exchange Online, permissions Exchange Online, Exchange Online management roles, Exchange Online management permissions, Exchange Online admin permissions, Exchange online features
ms.collection: 
- exchange-online
- M365-email-calendar
audience: ITPro
ms.service: exchange-online
manager: serdars

---

# Feature permissions in Exchange Online

The permissions required to perform tasks to manage Microsoft Exchange Online vary depending on the procedure being performed or the cmdlet you want to run.

For information about Exchange Online Protection (EOP) permissions, see [Feature Permissions in EOP](https://technet.microsoft.com/library/34674847-a6b7-4a7e-9eaa-b64f22bc150d.aspx).

To find out what permissions you need to perform the procedure or run the cmdlet, do the following:

1. In the table below, find the feature that is most related to the procedure you want to perform or the cmdlet you want to run.

2. Next, look at the permissions required for the feature. You must be assigned one of those role groups, an equivalent custom role group, or an equivalent management role. You can also click on a role group to see its management roles. If a feature lists more than one role group, you only need to be assigned one of the role groups to use the feature. For more information about role groups and management roles, see [Understanding Role Based Access Control](https://docs.microsoft.com/Exchange/understanding-role-based-access-control-exchange-2013-help).

3. Now, run the **Get-ManagementRoleAssignment** cmdlet to look at the role groups or management roles assigned to you to see if you have the permissions that are necessary to manage the feature.

    > [!NOTE]
    > You must be assigned the Role Management management role to run the **Get-ManagementRoleAssignment** cmdlet. If you don't have permissions to run the **Get-ManagementRoleAssignment** cmdlet, ask your Exchange administrator to retrieve the role groups or management roles assigned to you.

If you want to delegate the ability to manage a feature to another user, see [Delegate role assignments](https://docs.microsoft.com/Exchange/delegate-role-assignments-exchange-2013-help).

## Exchange Online permissions

You can use the features in the following table to manage your Exchange Online organization and recipients. Users who are assigned the View-Only Management role group can view the configuration of the features in the following table. For more information, see [View-only Organization Management](https://docs.microsoft.com/Exchange/view-only-organization-management-exchange-2013-help).

|**Feature**|**Permissions required**|
|:-----|:-----|
|Anti-malware|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Hygiene Management](https://technet.microsoft.com/library/fc0a9ec2-9c3d-42f6-8442-8603fb29d464.aspx)|
|Anti-spam|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Hygiene Management](https://technet.microsoft.com/library/fc0a9ec2-9c3d-42f6-8442-8603fb29d464.aspx)|
|Data loss prevention|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Compliance Management](https://technet.microsoft.com/library/b91b23a4-e9c7-4bd0-9ee3-ec5cb498da15.aspx)|
|Office 365 connectors|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx)|
|Journal archiving|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](https://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx)|
|Linked user|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](https://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx)|
|Mail flow|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx)|
|Mailbox settings|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](https://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx)|
|Microsoft Office 365 Message Encryption (OME)|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Compliance Management](https://technet.microsoft.com/library/b91b23a4-e9c7-4bd0-9ee3-ec5cb498da15.aspx) <br/> [Records Management](https://technet.microsoft.com/library/0e0c95ce-6109-4591-b86d-c6cfd44d21f5.aspx)|
|Message trace|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Compliance Management](https://technet.microsoft.com/library/b91b23a4-e9c7-4bd0-9ee3-ec5cb498da15.aspx) <br/> [Help Desk](https://technet.microsoft.com/library/e7958752-22e4-4155-a2fc-948099dec6f7.aspx)|
|Organization configuration|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx)|
|Outlook on thew web mailbox policies|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management|(http://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx)
|POP3 and IMAP4 permissions|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx)|
|Quarantine|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Hygiene Management](https://technet.microsoft.com/library/fc0a9ec2-9c3d-42f6-8442-8603fb29d464.aspx)|
|Subscriptions|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) <br/> [Recipient Management](https://technet.microsoft.com/library/669d602e-68e3-41f9-a455-b942d212d130.aspx) <br/> **Note**: A user can create subscriptions in their own mailbox. An administrator can't create subscriptions in another user's mailbox, but they can modify or delete subscriptions in another user's mailbox.|
|Supervision|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx)|
|View reports|[Organization Management](https://technet.microsoft.com/library/0bfd21c1-86ac-4369-86b7-aeba386741c8.aspx) - users have access to mailbox reports and mail protection reports. <br/> [View-Only Organization Management](https://technet.microsoft.com/library/c514c6d0-0157-4c52-9ec6-441d9a30f3df.aspx) - users have access to mailbox reports. <br/> [View-Only Recipients](https://technet.microsoft.com/library/37e66b92-81d3-412f-b7a9-e1bb8cbeb468.aspx) - users have access to mail protection reports. <br/> [Compliance Management](https://technet.microsoft.com/library/b91b23a4-e9c7-4bd0-9ee3-ec5cb498da15.aspx) - users have access to mail protection reports and Data Loss Prevention (DLP) reports (if their subscription has DLP capabilities).|
