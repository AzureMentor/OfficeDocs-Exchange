---
localization_priority: Normal
description: Learn about DLP policies in Exchange Server and Exchange Online, including what they contain and how to test them. You'll also learn about a new feature in Exchange DLP.
ms.topic: overview
author: msdmaguire
ms.author: dmaguire
ms.assetid: 7c8ed3c1-ca91-4d9b-b16b-0a2b8ac89730
ms.date: 7/11/2018
ms.reviewer: 
title: Data loss prevention
ms.collection:
- exchange-online
- M365-email-calendar
audience: ITPro
ms.service: exchange-online
manager: serdars

---

# Data loss prevention

Learn about DLP policies in Exchange Server and Exchange Online, including what they contain and how to test them. You'll also learn about a new feature in Exchange DLP.

Data loss prevention (DLP) is an important issue for enterprise message systems because of the extensive use of email for business critical communication that includes sensitive data. In order to enforce compliance requirements for such data, and manage its use in email, without hindering the productivity of workers, DLP features make managing sensitive data easier than ever before. For a conceptual overview of DLP, watch the following video.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/31f2b48e-93ed-4be3-b46d-e7230c0fed8f?autoplay=false]

DLP policies are simple packages that contain sets of conditions, which are made up of mail flow rule (also known as transport rule) conditions, exceptions, and actions that you create in the Exchange admin center (EAC) and then activate to filter email messages and attachments. You can create a DLP policy, but choose to not activate it. This allows you to test your policies without affecting mail flow. DLP policies can use the full power of existing mail flow rules. In fact, a number of new types of mail flow rules have been created in Microsoft Exchange Server and Exchange Online in order to accomplish new DLP capability. One important new feature of mail flow rules is a new approach to classifying sensitive information that can be incorporated into mail flow processing. This new DLP feature performs deep content analysis through keyword matches, dictionary matches, regular expression evaluation, and other content examination to detect content that violates organizational DLP policies. For more information about mail flow rules, see [Mail flow rules (transport rules) in Exchange Online](../mail-flow-rules/mail-flow-rules.md), and [Integrating sensitive information rules with mail flow rules in Exchange Online](integrate-sensitive-information-rules.md). You can also manage your DLP policies by using Exchange Online PowerShell cmdlets. For more information about policy and compliance cmdlets, see [Messaging Policy and Compliance Cmdlets](https://technet.microsoft.com/library/78ed4e33-f031-40fe-b632-9b15e3234e77.aspx).

In addition to the customizable DLP policies themselves, you can also inform email senders that they may be about to violate one of your policies, even before they send an offending message. You can accomplish this by configuring Policy Tips. Policy Tips are similar to MailTips, and can be configured to present a brief note in the Microsoft Outlook 2013 client that provides information about possible policy violations to a person creating a message. In Exchange Online and in Exchange Server, Policy Tips are also displayed in Outlook on the web (formerly known as Outlook Web App) and OWA for Devices. For more information, see [Policy Tips](policy-tips.md).

> [!NOTE]
> DLP is a premium feature that requires an Exchange Online Plan 2 subscription. For more information, see [Exchange Online Licensing](https://go.microsoft.com/fwlink/p/?linkid=286154). > Messages sent between on-premises users in a hybrid deployment do not have Exchange Online DLP policies applied, because the message doesn't leave the on-premises infrastructure.

Looking for management tasks related to Data Loss Prevention? See [DLP Procedures](https://technet.microsoft.com/library/e2f575aa-552e-4dcc-8d7b-1ffd697d67df.aspx) (Exchange Server) or [DLP Procedures](https://technet.microsoft.com/library/925290cc-f3b4-401e-b6c7-9a216a726f17.aspx) (Exchange Online).

## Establish policies to protect sensitive data
<a name="dlp_establish"> </a>

The data loss prevention features can help you identify and monitor many categories of sensitive information that you have defined within the conditions of your policies, such as private identification numbers or credit card numbers. You have the option of defining your own custom policies and mail flow rules or using the pre-defined DLP policy templates provided by Microsoft in order to get started quickly. For more information about the policy templates that are included, see [DLP policy templates supplied in Exchange](dlp-policy-templates.md). A policy template includes a range of conditions, rules, and actions that you can choose from in order to create and save an actual DLP policy that will help you inspect messages. The policy templates are models from which you can select or build your own specific rules to create a policy that meets your needs for data loss prevention.

Three different methods exist for you to begin using DLP:

1. **Apply an out-of-the-box template supplied by Microsoft**: The quickest way to start using DLP policies is to create and implement a new policy using a template. This saves you the effort of building a new set of rules from nothing. You will need to know what type of data you want to check for or which compliance regulation you are attempting to address. You will also need to know your organizations expectations for processing such data. More information at [DLP policy templates supplied in Exchange](dlp-policy-templates.md) and [Create a DLP policy from a template](create-dlp-policy-from-template.md).

2. **Import a pre-built policy file from outside your organization**: You can import policies that have already been created outside of your messaging environment by independent software vendors. In this way you can extend the DLP solutions to suit your business requirements. More information at [Policies from Microsoft Partners](https://technet.microsoft.com/library/0f95336e-b3ef-4041-9604-adf7b0b335fe.aspx), [Define Your Own DLP Templates and Information Types](https://technet.microsoft.com/library/f4622dba-3347-4758-b4a2-f01b043c908c.aspx), and [Import a DLP Policy From a File](https://technet.microsoft.com/library/83f49dbd-f9b1-498e-b548-1529c5e1ccdb.aspx).

3. **Create a custom policy without any pre-existing conditions**: Your enterprise may have its own requirements for monitoring certain types of data known to exist within a messaging system. You can create a custom policy entirely on your own in order to start checking and acting upon your own unique message data. You will need to know the requirements and constraints of the environment in which the DLP policy will be enforced in order to create such a custom policy. More information at [Create a custom DLP policy](create-custom-dlp-policy.md).

After you have added a policy, you can review and change its rules, make the policy inactive, or remove it completely. The procedures for these actions are provided in the [Manage DLP Policies](https://technet.microsoft.com/library/ba81fabd-7f7f-4ef7-968f-ce851ada9d70.aspx) topic.

## Sensitive information types in DLP policies
<a name="dlp_senstypes"> </a>

When you create or change DLP policies, you can include rules that include checks for sensitive information. The sensitive information types listed in the [Sensitive Information Types Inventory](https://technet.microsoft.com/library/98b81f9c-87bb-4905-8e53-04621c3ae74d.aspx) topic are available to be used in your policies. The conditions that you establish within a policy, such as how many times something has to be found before an action is taken or exactly what that action is can be customized within your new custom policies in order to meet your specific policy requirements. For more information about creating DLP policies see, [Create a custom DLP policy](create-custom-dlp-policy.md). For more information about the full suite mail flow rules, see [Mail flow rules (transport rules) in Exchange Online](../../security-and-compliance/mail-flow-rules/mail-flow-rules.md).

To make it easy for you to make use of the sensitive information-related rules, Microsoft has supplied policy templates that already include some of the sensitive information types. You cannot add conditions for all of the sensitive information types listed here to policy templates however, because the templates are designed to help you focus on the most-common types of compliance-related data within your organization. For more information about the pre-built templates, see [DLP policy templates supplied in Exchange](dlp-policy-templates.md). You can create numerous DLP policies for your organization and have them all enabled so that many disparate types of information are examined. You can also create a DLP policy that is not based on an existing template. To begin creating such a policy, see [Create a custom DLP policy](create-custom-dlp-policy.md). For more information about sensitive information types, see [Sensitive Information Types Inventory](https://technet.microsoft.com/library/98b81f9c-87bb-4905-8e53-04621c3ae74d.aspx).

## Policy Tips notify users about sensitive content expectations
<a name="dlp_tips"> </a>

You can use Policy Tip notification messages to inform email senders about possible compliance issues while they are composing an email message. When you configure a Policy Tip in a DLP policy, the notification message will only show up if something in the sender's email message meets the conditions described in your policy. Policy Tips are similar to MailTips that were introduced in Microsoft Exchange 2010. For more information, see [Policy Tips](policy-tips.md).

## Detecting sensitive information along with traditional message classification
<a name="dlp_detectingsens"> </a>

Exchange Server and Exchange Online present a new method of helping you manage message and attachment data when compared with traditional message classification. A key factor in the strength of a DLP solution is the ability to correctly identify confidential or sensitive content that may be unique to the organization, regulatory needs, geography, or other business needs. Exchange Server can achieve this by using a new architecture for deep content analysis coupled with detection criteria that you establish through rules in your DLP policies. Helping prevent data loss in Exchange Server relies on configuring the correct set of sensitive information rules so that they provide a high degree of protection while minimizing inappropriate mail flow disruption with false positives and negatives. These types of rules, referred to throughout the DLP information as sensitive information detection, function within the framework offered by mail flow rules in order to enable DLP capabilities.

To learn more about these new features, see [Integrating sensitive information rules with mail flow rules in Exchange Online](integrate-sensitive-information-rules.md). The traditional message classification fields can still be applied to messages in Exchange and these can be combined with the new sensitive information detection either together within a single DLP policy or running concurrently so they are evaluated independently within Exchange. To learn more about the legacy Exchange 2010 message classifications, see [Understanding Message Classifications](https://go.microsoft.com/fwlink/p/?LinkId=266612).

## Information about DLP-processed messages
<a name="dlp_information"> </a>

For Exchange Server to obtain information about messages and DLP policy detections in your environment, see [DLP policy detection reports](https://technet.microsoft.com/library/5c3f1cf6-d8c7-4d83-bb24-641ea9d50cbc.aspx) and [Create incident reports for DLP policy detections](https://technet.microsoft.com/library/8e807f94-384c-43f5-be6f-06c5587175a0.aspx). Data related to DLP detections, is highly integrated into the delivery reports message tracking tool of Exchange Server.

For Exchange Online, see [DLP policy detection reports](https://technet.microsoft.com/library/84295dda-5bf7-4fa5-a1ee-3f761501cfe8.aspx) and [Create incident reports for DLP policy detection](https://technet.microsoft.com/library/f80d2505-e055-4ed1-896f-8946545d29f6.aspx).

## Installation prerequisites
<a name="dlp_install"> </a>

In order to make use of DLP features, you must have Exchange Server or Exchange Online configured with at least one sender mailbox. Data Loss Prevention is a premium feature that requires an Enterprise Client Access License (CAL). For more information about getting started with Exchange Server, see [Planning and Deployment](https://technet.microsoft.com/library/692c59e3-f0b0-4cef-a66e-751aa740abae.aspx). For more information about getting started with Exchange Online, see [Exchange Online](../../exchange-online.md).

## For more information
<a name="dlp_moreinfo"> </a>

Exchange Server

- [Messaging Policy and Compliance](https://technet.microsoft.com/library/65f20a20-27a4-4f6e-9b27-f8705d65b8d9.aspx)

- [DLP Procedures](https://technet.microsoft.com/library/e2f575aa-552e-4dcc-8d7b-1ffd697d67df.aspx)

- [DLP policy detection reports](https://technet.microsoft.com/library/5c3f1cf6-d8c7-4d83-bb24-641ea9d50cbc.aspx)

- [Messaging Policy and Compliance Cmdlets](https://technet.microsoft.com/library/78ed4e33-f031-40fe-b632-9b15e3234e77.aspx)

Exchange Online

- [Security and compliance for Exchange Online](../../security-and-compliance/security-and-compliance.md)

- [DLP Procedures](https://technet.microsoft.com/library/925290cc-f3b4-401e-b6c7-9a216a726f17.aspx)

- [DLP policy detection reports](https://technet.microsoft.com/library/84295dda-5bf7-4fa5-a1ee-3f761501cfe8.aspx)
