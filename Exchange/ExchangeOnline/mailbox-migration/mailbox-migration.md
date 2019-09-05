---
localization_priority: Normal
ms.topic: conceptual
author: msdmaguire
ms.author: dmaguire
ms.assetid: 0a4913fe-60fb-498f-9155-a86516418842
ms.date: 9/19/2018
ms.reviewer: 
description: Learn all the ways admins can use to migrate user mailboxes to Office 365.
title: Ways to migrate multiple email accounts to Office 365
ms.collection: 
- exchange-online
- M365-email-calendar
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
audience: Admin
ms.custom:
- Adm_O365
- Adm_O365_Setup
ms.service: exchange-online
manager: serdars

---

# Ways to migrate multiple email accounts to Office 365

Your organization can migrate email to Office 365 from other systems. Your administrators can [Migrate mailboxes from Exchange Server](mailbox-migration.md#StagedorCutover) or [Migrate email from another IMAP-enabled email system](mailbox-migration.md#IMAP). And your users can [Have users import their own email](mailbox-migration.md#Import) their own email, contacts, and other mailbox information to an Office 365 mailbox created for them. Your organization also can [Work with a partner to migrate email](mailbox-migration.md#Partner) to migrate email.

Before you start an email migration, review [limits](https://go.microsoft.com/fwlink/p/?LinkID=328224) and [best practices](https://go.microsoft.com/fwlink/p/?LinkID=392945) for Exchange Online to make sure you get the performance and behavior you expect after migration.

See [Decide on a migration path](decide-on-a-migration-path.md) or [Exchange migration advisors](https://aka.ms/office365setup) for help with choosing the best option for your organization.

> [!TIP]
> Another option available to assist you with your email migration is [FastTrack Center Benefit for Office 365](https://docs.microsoft.com/fasttrack/fasttrack-benefit-overview). FastTrack specialists can help you plan and perform your migration. For more information, see [Data Migration](https://docs.microsoft.com/fasttrack/data-migration).

You can also view an overview video:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/226b533f-a08b-476f-b1ca-1c0e96b1c85b?autoplay=false]

## Migrate mailboxes from Exchange Server
<a name="StagedorCutover"> </a>

For migrations from an existing on-premises Exchange Server environment, an administrator can migrate all email, calendar, and contacts from user mailboxes to Office 365.

![An administrator performs a staged or cutover migration to Office 365. All email, contacts, and calendar information can be migrated for each mailbox.](media/1e539e0e-bdc6-426b-aff1-2077f6f76eda.png)

There are three types of email migrations that can be made from an Exchange Server:

- **Migrate all mailboxes at once (cutover migration) or Express migration**

    Use this type of migration if you're running Exchange 2003, Exchange 2007, Exchange 2010, or Exchange 2013, and if there are fewer than 2000 mailboxes. You can perform a cutover migration by starting from the Exchange admin center (EAC); see [Perform a cutover migration to Office 365](cutover-migration-to-office-365.md). See [Use express migration to migrate Exchange mailboxes to Office 365](use-minimal-hybrid-to-quickly-migrate.md) to use the Express migration.

    > [!IMPORTANT]
    > With cutover migration, you can move up to 2000 mailboxes, but due to length of time it takes to create and migrate 2000 users, it is more reasonable to migrate 150 users or less.

- **Migrate mailboxes in batches (staged migration)**

    Use this type of migration if you're running Exchange 2003 or Exchange 2007, and there are more than 2,000 mailboxes. For an overview of staged migration, see [What you need to know about a staged email migration to Office 365](what-to-know-about-a-staged-migration.md). To perform the migration tasks, see [Perform a staged migration of Exchange Server 2003 and Exchange 2007 to Office 365](perform-a-staged-migration/perform-a-staged-migration.md).

- **Migrate using an integrated Exchange Server and Office 365 environment (hybrid)**

    Use this type of migration to maintain both on-premises and online mailboxes for your organization and to gradually migrate users and email to Office 365. Use this type of migration if:

  - You have Exchange 2010 and more than 150-2,000 mailboxes.

  - You have Exchange 2010 and want to migrate mailboxes in small batches over time.

  - You have Exchange 2013.

    For more information, see [Plan an Exchange Online hybrid deployment in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=517633).

## Use Office 365 Import Service to migrate PST-files
<a name="StagedorCutover"> </a>

If your organization has many large PST files, you can use the Office 365 Import Service to migrate email data to Office 365.

![An administrator migrates PST files to Office 365.](media/23459be8-cf49-41f9-85fc-14e4ad2c06f3.png)

You can use the Office 365 Import Service to either upload the PST files through a network, or to mail the PST files in a drive that you prepare.

For instructions, see [Office 365 Import Service](https://go.microsoft.com/fwlink/p/?LinkId=544944).

## Migrate email from another IMAP-enabled email system
<a name="IMAP"> </a>

You can use the Internet Message Access Protocol (IMAP) to migrate user email from Gmail, Exchange, Outlook.com, and other email systems that support IMAP migration. When you migrate the user's email by using IMAP migration, only the items in the users' inbox or other mail folders are migrated. Contacts, calendar items, and tasks can't be migrated with IMAP, but they can be by a user.

IMAP migration also doesn't create mailboxes in Office 365. You'll have to create a mailboxfor each user before you migrate their email.

![An administrator performs an IMAP migration to Office 365. All email, but not contacts or calendar information, can be migrated for each mailbox.](media/624879f0-305f-4893-b4c2-c64736a40d94.png)

To migrate email from another mail system, see [Migrate your IMAP mailboxes to Office 365](migrating-imap-mailboxes/migrating-imap-mailboxes.md). After the email migration is done, any new mail sent to the source email isn't migrated.

## Have users import their own email
<a name="Import"> </a>

Users can import their own email, contacts, and other mailbox information to Office 365. See [Migrate email and contacts to Office 365](https://support.office.com/article/a3e3bddb-582e-4133-8670-e61b9f58627e) to learn how.

![A user can import email, contacts, and calendar information to Office 365.](media/86255b6b-a1bf-413d-b3f2-95ad43a628c0.png)

## Work with a partner to migrate email
<a name="Partner"> </a>

If none of the types of migrations described will work for your organization, consider working with a partner to migrate email to Office 365.

|**Method**|**Description**|
|:-----|:-----|
|![Use third-party migration tools to migrate mailboxes to Office 365](media/e0d851ac-72c5-49e5-b759-f1083c912f03.png)|**Use a third-party email migration tool** <br/> Migration tools can help speed up and simplify email migration. You'll find a list of tools in the [Office 365 Marketplace](https://go.microsoft.com/fwlink/p/?LinkId=785068).|
|![Hire a partner to help you deploy Office 365](media/60914e97-f5fe-4dff-9e96-a23de8aa2879.png)|**Hire a partner to help migrate your email** <br/> You'll find a list of partners in the [Office 365 Marketplace](https://go.microsoft.com/fwlink/p/?LinkId=620000).|

## Related Topics
<a name="Partner"> </a>

[Use PowerShell for email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=615247)
