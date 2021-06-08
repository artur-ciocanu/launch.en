---
title: Link a DTM Embed Code
description: Learn how to link a Dynamic Tag Management (DTM) embed code using Adobe Experience Platform Launch.
exl-id: 467742f6-63ee-4a11-8d53-2ecb5b9d0414
---
# Link a DTM embed code

>[!NOTE]
>
>Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../../launch-term-updates.md) for a consolidated reference of the terminology changes.

Linking embed codes primarily applies to Dynamic Tag Management (DTM) and Adobe Experience Platform Launch users who use built-in Akamai hosting. Those who are self-hosting, please see the [self-hosting section](#self-hosting) at the end of this article.

## Embed Code {#embed-code}

A DTM embed code is a `<script>` tag that you embed in the HTML of your web page.

This `<script>` tag retrieves a JavaScript file published by DTM and loads it on the page. This file is the DTM library file, commonly called a container tag. This container tag contains all the tools, data element definitions, rules logic, and code that you define inside of DTM.

DTM publishes this container tag file to the web host you specified, which is either an Akamai location or your own FTP location. The embed code that DTM provides is based on this host location.

When a user visits your site in a browser, the browser requests the DTM file from this server, using the embed code, and loads it.

In the diagram below, Step 1 shows DTM publishing the container tag to your specified web host. In Step 2, the browser requests the container tag, using the embed code, and the host responds with the published file.

![](/help/images/dtm_publishing.png)

## Linking Embed Codes {#linking-embed-codes}

The linking process allows you to take the DTM Production embed code, with its matching host location, and use that same embed code with your [!DNL Platform Launch]  production environment.

If you do this, DTM and [!DNL Platform Launch]  share the server location and the container tag file name.

When you publish in [!DNL Platform Launch] , the [!DNL Platform Launch]  container tag file overwrites the DTM file, so when the browser requests the file from the server, the [!DNL Platform Launch]  file is returned.

In the diagram below, Step 3 represents [!DNL Platform Launch]  publishing its container tag over the top of the DTM container tag (from Step 1). When Step 2 occurs, it gets the [!DNL Platform Launch]  container tag instead.

![](/help/images/launch_publishing.png)

>[!IMPORTANT]
>
>This overwriting works both ways. If you publish [!DNL Platform Launch] , then subsequently publish from DTM, the DTM container tag overwrites the [!DNL Platform Launch]  one. You have two systems publishing to the same location. This means you don't have to change the code on your page, but it also means you need to be careful when you publish. It's recommended that you disable your DTM property to prevent this situation.

## Linking Prerequisites {#linking-prerequisites}

Before you link your embed code:

* Your DTM company must be connected to the same Experience Cloud Organization as [!DNL Platform Launch] .
* Your user account must have the Manage Environments right in [!DNL Platform Launch]  and the Admin right in DTM.
* Your DTM property must not already be linked to a different [!DNL Platform Launch]  property.

## How to Link the Embed Code {#how-to-link-the-embed-code}

1. In [!DNL Platform Launch] , open the [!UICONTROL Environments] tab.
1. Create a new Production environment.
1. Give your environment a name.
1. Toggle the **[!UICONTROL Link DTM embed code]** option on.
1. Paste your DTM production embed code into the **[!UICONTROL DTM Embed Code]** field in [!DNL Platform Launch] .
1. Finish configuring your [!DNL Platform Launch]  Production environment (archive setup, etc).
1. Select **[!UICONTROL Save]**.

[!DNL Platform Launch]  validates a number of things and tells you whether linking was successful.

>[!IMPORTANT]
>
>You can only have one Production environment in [!DNL Platform Launch] . If you have already created one on this property, you need to delete the existing Production environment so you can create a new linked environment. The new one does not have the same embed code as the old one, so don't do this unless you are familiar with the process.

## Recommended Test Process {#recommended-test-process}

If you use embed code linking, the process is mostly the same as without it, but with some highlighted differences:

1. Create your property, install an extension, create data elements, and create rules in [!DNL Platform Launch] , as you normally would.
1. Create your Development and Staging environments in [!DNL Platform Launch]  as usual.
1. ​Create a linked Production environment as described above.
1. Create your library in [!DNL Platform Launch]  as usual.
1. Test in Development, submit, test in Staging, and approve as usual.
1. Publish. The [!DNL Platform Launch]  container tag overwrites the DTM container tag and any browser with this embed code retrieves the [!DNL Platform Launch]  container tag.
1. Disable your DTM property to prevent accidentally publishing the DTM file over the top of the [!DNL Platform Launch]  file.

Step 7 can be done any time after Step 3 has been performed.

## Self-hosting {#self-hosting}

DTM also supports self-hosting of the DTM container tag file. There are two methods to accomplish this:

* FTP Delivery
* Library Download

In either case, it doesn't make much sense to migrate the embed code. Nothing will break if you try it. It's recommended that you not use this option and set up your hosts and environments manually.

### FTP Delivery {#ftp-delivery}

Due to the differences in setup between FTP and SFTP, DTM and [!DNL Platform Launch]  cannot perform automated migrations of these settings.

If you are using this method for delivery of the container tag, it's recommended that you move to SFTP in [!DNL Platform Launch] . You can create an [SFTP host](/help/launch-reference/publishing/hosts/sftp-host.md) and use this for any environment that you choose.

### Library Download {#library-download}

In [!DNL Platform Launch] , downloading the library no longer exists as a separate option. If you use a library download in DTM, we recommend you skip the embed code migration and set up your Production environment with an Adobe Managed host and Archive enabled.

You can continue to use the same embed code that you use with DTM, but you are responsible for moving the library to your own servers with the correct file name.
