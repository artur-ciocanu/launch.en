---
title: Release an Extension
description: Learn how to privately or publicly release an Adobe Experience Platform Launch extension.
exl-id: 64e40955-82a7-4985-bf67-edc702a3eebb
---
# Release an extension

Once you've completed testing and documenting, you are ready to release. There are currently two types of releases that you can perform:

* **Private release**: The completed extension is available to all properties within your company, but is not available to any other companies in Adobe Experience Platform Launch.
* **Public release**: The completed extension is available in the public marketplace for all Platform Launch users.

>[!NOTE]
>
>Once you have released your extension, you can no longer make changes to it and you cannot unrelease it.  Once released, bug fixes and feature additions are accomplished by `POST`ing a new version of your extension package and following the above testing and release steps on that new version.

You must release your extension as a private extension before you can release it publicly.

## Private release

The easiest way to release your extension to private availability is to use the [Platform Launch Extension Releaser](https://www.npmjs.com/package/@adobe/reactor-releaser). More instructions are found within its documentation.

If you'd like to release your extension to private availability using the API directly, see the example call for [privately releasing an extension package](https://developer.adobelaunch.com/api/reference/1.0/extension_packages/release_private/) in the API docs for more detail.

## Public release

Once you have completed the private release, you can ask Adobe to release it publicly.  This will make your extension available in the public catalog.  Any Platform Launch user can install your extension to any property.

Please complete the [public release request form](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=7DRB5U) to begin the release process.
