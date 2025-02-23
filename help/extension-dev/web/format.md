---
title: Library Modules in Web Extensions
description: Learn how to format library modules for web extensions in Adobe Experience Platform Launch.
exl-id: 17fb6e5e-1e22-4192-a4a3-018f63061ef6
---
# Library modules in web extensions

>[!IMPORTANT]
>
>This document covers the library module format for web extensions. If you are developing an edge extension, see the guide on [formatting edge extension modules](../edge/format.md) instead.

A library module is a piece of reusable code provided by an extension that is emitted inside the Adobe Experience Platform Launch runtime library (the library that runs on the client's website). For example, a `gesture` event type will have a library module that will run on the client's website and detects user gestures.

The library module is structured as a [CommonJS module](http://wiki.commonjs.org/wiki/Modules/1.1.1). Within a CommonJS module, the following variables are available for usage:

## [!DNL require]

A `require` function is available for you to access:

1. Core modules provided by Platform Launch. These modules may be accessed by using `require('@adobe/reactor-name-of-module')`. See the document on available [core modules](./core.md) for more information.
2. Other modules within your extension. Any module in your extension can be accessed via a relative path. The relative path must begin with `./` or `../`.

Example usage:

```javascript
var cookie = require('@adobe/reactor-cookie');
cookie.set('foo', 'bar');
```

## [!DNL module]

A free variable named `module` is available which allows you to export the module's API.

Example usage:

```javascript
module.exports = function(…) { … }
```

## [!DNL exports]

A free variable named `exports` is available which allows you to export the module's API.

Example usage:

```javascript
exports.sayHello = function(…) { … }
```

This is an alternative to `module.exports` but is more limited in its usage. Please read [Understanding module.exports and exports in node.js](https://www.sitepoint.com/understanding-module-exports-exports-node-js/) for a better understanding of the differences between `module.exports` and `exports` and the related caveats with using `exports`. When in doubt, make your life easier and use `module.exports` rather than `exports`.

## Execution and caching

When the Platform Launch runtime library runs, modules will be immediately "installed" and their exports cached. Assuming the following module:

```javascript
console.log('runs on startup');

module.exports = function(settings) {
  console.log('runs when necessary');
}
```

`runs on startup` will be logged immediately whereas `runs when necessary` will only be logged once the exported function is called by the Platform Launch engine. While it may be unnecessary for the purpose of your particular module, you may take advantage of this by performing any setup necessary before exporting the function.
