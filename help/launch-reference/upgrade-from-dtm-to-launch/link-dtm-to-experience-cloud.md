---
title: Link DTM to Experience Cloud
description: Learn how to link Dynamic Tag Management (DTM) to Adobe Experience Cloud using Adobe Experience Platform Launch.
exl-id: aabac85b-b714-4f5b-a772-e8ed551eaaa4
---
# Link DTM to Experience Cloud

>[!NOTE]
>
>Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../../launch-term-updates.md) for a consolidated reference of the terminology changes.

If you've been using Dynamic Tag Management (DTM) for a while, it's possible that your company's account is older than the Experience Cloud (or even the Marketing Cloud). Unless you've already gone through the process to link your DTM account to the Experience Cloud, this work still lies ahead of you.

This document explains the reasons you may want to do that work and what you need to know about linking to the Experience Cloud.

## Why would I link to Experience Cloud?

The most common reason to link your DTM account to the Experience Cloud is in preparation for a [migration to Adobe Experience Platform Launch](/help/launch-reference/upgrade-from-dtm-to-launch/overview.md). [!DNL Platform Launch]  permissions are managed through the Experience Cloud and migrations can only be performed between DTM and [!DNL Platform Launch]  when company accounts are linked to the same Experience Cloud _Organization_.

Linking can also be a good idea if you want to improve your governance. When linked to the Experience Cloud, all permissions for Adobe products are managed in a central place. If you have a new employee (or need to remove permissions for an old one), there's a single place to take care of that for all Adobe products.

## What changes when I link to Experience Cloud?

When you link or unlink your DTM account from the Experience Cloud the only thing that changes is the way you login to DTM. Your DTM properties, tools, rules, data elements, approval and publishing queues, and your published libraries are all unaffected by this process.

Once the accounts are linked, DTM will rely on the Experience Cloud to tell it which users are authorized to access the tool and which users have permission to perform which actions instead of looking inside its own database. This means that the existing permissions you set up inside DTM go away and you have to reassign user permissions from inside the [Admin Console](https://adminconsole.adobe.com) in the Experience Cloud.

Depending on how many users you have and the complexity of your permissions structure, this can either go very quickly or take you some time.

>[!NOTE]
>
>For users who belong to multiple DTM companies, please note that an individual email can only be associated with one type of account (linked DTM accounts or standalone DTM accounts). If you need to access one or more linked DTM companies and one or more standalone DTM companies, you'll need to use different email addresses.

## How do I link my company's DTM account to Experience Cloud?

Linking your DTM account to the Experience Cloud is not currently a self-service process. You can initiate this process by talking to your Adobe rep (if you have one) or Client Care. Maybe even give them a link to this article.

Simply explain to them what you need (I need to link my DTM account to the Experience Cloud). They will then make a request to Adobe's provisioning team. That team will make sure there are no hidden issues (for example, another DTM account is already linked to your Experience Cloud account) and then perform the linking. These requests are usually fulfilled within 2-3 business days, so plan accordingly.
