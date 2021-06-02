---
title: Extension Configuration
description: Learn how to configure a tag extension in Adobe Experience Platform Data Collection to gather global settings from a user.
exl-id: 60081c35-4fa7-469e-affa-1b79c5e46a51
---
# Extension configuration

>[!NOTE]
>
>Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../launch-term-updates.md) for a consolidated reference of the terminology changes.

Extension configuration is the manner by which an extension gathers global settings from a user. For example, consider an extension that allows the user to send a beacon using a Send Beacon action, and the beacon must always contain an account ID. We don't want to trouble users by asking them for the account ID each time they configure a Send Beacon action. Instead, the extension should ask for the account ID once from the extension configuration view. Each time a beacon is to be sent, the Send Beacon action library module can pull the account ID from the extension configuration and add it to the beacon.

In Adobe Experience Platform Data Collection, when users install an extension to a tags property, they will be shown the extension configuration view which your extension will provide. They cannot complete installing the extension without completing extension configuration. See the document on [views](./web/views.md) to learn how to create a view for extension configuration.

After settings are saved from an extension configuration view, they will be emitted in the tag runtime library. You can then access these settings from extension library modules by calling [`turbine.getExtensionSettings()`](./turbine.md#get-extension-settings).

Extension configuration is an optional feature that you may choose not to leverage.
