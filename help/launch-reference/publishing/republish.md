---
title: Republish a Library
description: Learn how to republish a previous library in Adobe Experience Platform Launch.
exl-id: eb112f48-a70c-4365-8ae6-148f26601f27
---
# Republish a library

>**Note**: Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../../launch-name-updates) for a consolidated reference of the terminology changes.

The five most recent libraries that have been published to your production environment on a Web property are available for later retrieval.  

This feature is helpful when you find a bug in your production library and need to rollback to a known good state immediately.

The retrieval process depends on your environment settings at the time the library was originally published. This is important because retrieving an archived library does not change anything on your live site, while retrieving a regular library would.

The following options are available:

* **Host: Managed by [!DNL Adobe], Archive: Off:** If you are using the Managed by [!DNL Adobe] host and you are not archiving your library, you can republish these older libraries.

* **Host: Managed by [!DNL Adobe], Archive: On:** If you are using the Managed by [!DNL Adobe] host and you are archiving your library, then you can download these older libraries.

* **Host: SFTP, Archive: On or Off:** If you are using the SFTP host, it is assumed that you have your own archival strategies in place and no retrieval options are available.

Retrieval options for mobile properties are not yet available.

## Republishing

Each [!DNL Adobe Experience Platform Launch] environment provides a link to a [!DNL Platform Launch] library file. Any library that you build in that environment is referenceable with that link.

When you build to a development or staging environment, the old build is cleaned up and the new build is deployed. For your production environment, this link is updated to point to the latest build, but the five most recent builds are kept around before they are cleaned up.

These five most recent builds in your production environment are the ones that are available for retrieval.

When you republish an older library, [!DNL Platform Launch] updates the environment link to point to one of these older builds that hasn't been cleaned up yet.  [!DNL Platform Launch] also issues a purge request to the CDN edge nodes cache to indicate that the library has been updated and a fresh copy should be retrieved from the origin.

This means that when you republish an older library:

* No changes are made to any of the resources (or historical revisions) in your Platform Launch property

* The way that development and staging environments calculate what is upstream does not change

Consider the scenario when you roll back because of a problem with a specific rule. The rule revision that is now in production might, for example, be three revisions old.  When you view that rule in [!DNL Platform Launch] to fix it, it still reflects the latest changes saved rather than what is currently in production.

For this reason, [!DNL Platform Launch] notifies you that a property is in a republished state as a reminder that what you're seeing in the [!DNL Platform Launch] interface is a little farther removed from Production than usual.  This notification is dismissable and appears once per browser session the first time you view the property.

### How to Republish an older library

![Republish a library](assets/retrieve_republish.png)

From the Publishing screen:

1. Find the library in the Published column that you'd like to republish.
2. Select the ellipsis (`...`) in the upper-right corner of the Library card.
3. Select **[!UICONTROL Republish]**.

## Download

Downloading an Archived library is more straightforward.  You aren't directly referencing these .zip files anywhere, so you can simply download the older library to your computer and run your usual process.

### How to Download an older library

![Download a library](assets/retrieve_download.png)

From the Publishing screen:

1. Find the library in the Published column that you'd like to download.
2. Select the ellipsis (`...`) in the upper-right corner of the Library card.
3. Select **[!UICONTROL Download]**.
