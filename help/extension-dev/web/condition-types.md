---
title: Condition Types for Web Extensions
description: Learn how to define a condition-type library module for a web extension in Adobe Experience Platform Launch.
exl-id: 3a515c93-f453-49b6-8832-92a51699ced3
---
# Condition types for web extensions

>**Note**: Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../../launch-name-updates) for a consolidated reference of the terminology changes.

A condition type library module has one goal: evaluate whether something is true or false. What it evaluates is up to you.

>[!NOTE]
>
>This document covers condition types for web extensions. If you are developing an edge extension, see the guide on [condition types for edge extensions](../edge/condition-types.md) instead.
>
>This document also assumes you are familiar with library modules and how they are integrated in Platform Launch extensions. If you require an introduction, see the overview on [library module formatting](./format.md) before returning to this guide.

For example, if you wanted to evaluate whether the user is on the host `example.com`, your module may look like this:

```js
module.exports = function(settings) {
  return document.location.hostname === 'example.com';
};
```

Now, consider a situation where you want to make the hostname configurable by the Adobe Experience Platform Launch user. You may allow the user to input a hostname and then save the hostname to the settings object. The object might look something like this:

```js
{
  "hostname": "example.com"
}
```

In order to operate on the user-defined hostname, your module would need to change to this:

```js
module.exports = function(settings) {
  return document.location.hostname === settings.hostname;
};
```

## Contextual event data

A second argument is passed to your module which contains contextual information regarding the event that fired the rule. It may be beneficial in certain cases and can be accessed as follows:

```js
module.exports = function(settings, event) {
  // event contains information regarding the event that fired the rule
};
```

The `event` object must contain the following properties:

| Property | Description |
| --- | --- |
| `$type` | A string describing the extension name and event name, joined using a period. For example, `youtube.play`. |
| `$rule` | An object containing information about the currently executing rule. The object must contain the following sub-properties:<ul><li>`id`: The ID of the currently executing rule.</li><li>`name`: The name of the currently executing rule.</li></ul> |

The extension providing the event type that triggered the rule may optionally add any other useful information to this `event` object.
