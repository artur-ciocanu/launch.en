---
title: Shared Modules in Web Extensions
description: Learn how to defined shared library modules in your Adobe Experience Platform Launch web extensions.
---

# Shared modules in web extensions

A shared module is a mechanism by which you can communicate with other extensions. In JavaScript implementations, all shared modules are instantiated using the [`getSharedModule`](../turbine.md#shared) method provided by the `turbine` free variable.

When developing your own Platform Launch extension, you can define any shared modules you want it to provide. For example, you can create a module that loads a user ID asynchronously and then shares the user ID with any other extension via a [promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise):

```javascript
var userIdPromise = new Promise(/* load user id, then resolve promise */);
module.exports = userIdPromise;
```

In the [extension manifest](../manifest.md) you have to provide a name for this shared module. If you name it `user-id-promise`, a different extension could then access this shared module as follows:

```javascript
var userIdPromise = turbine.getSharedModule('user-extension', 'user-id-promise');
```

Shared modules can be anything you would typically be able to export from a CommonJS module (such as functions, objects, strings, numbers, or booleans).
