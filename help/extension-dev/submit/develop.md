---
title: Develop an Extension
description: This document provides a general overview of the extension development process, with links to further documentation for more detailed processes.
exl-id: f4b6173e-6690-438b-a363-05e364b32a0e
---
# Develop an extension

>[!NOTE]
>
>Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../../launch-term-updates.md) for a consolidated reference of the terminology changes.

An extension should be thought of as a (small) product with its own requirements. Determining how an Adobe Experience Platform data collection user will want to use your extension can help you sort the functionality into what event types, condition types, action types, and data element types your extension should provide.

With that knowledge you can plan out what components should be provided in your extension.

## Guides

With a plan in place, these guides can help you understand the extension development process:

- The [getting started guide](../getting-started.md) and most of the other documents under **Extension development** in the left navigation are great reference material for understanding what extensions can do, how user information is stored and passed between your extension and tags in Adobe Experience Platform, how your code is bundled into libraries within Adobe Experience data collection, and how your extension code is interpreted and used at runtime in the browser.
- The [extension tutorial video](https://youtu.be/rxjtC9o4rl0) is a great place to start.
- The [Introduction to Extensions](https://www.youtube.com/playlist?list=PLOdw8u2F8CIgynzKrPEwCPuDxzHW1WP5m) YouTube playlist walks through the process of creating extension packages.
- [Understanding JSON Schema](https://spacetelescope.github.io/understanding-json-schema/index.html#) article.
- [JSON Lint/Validator](http://jsonlint.com/).
- [JSON Viewer](https://chrome.google.com/webstore/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh) Chrome extension to highlight & print JSON & JSONP.
- [jsonschema.net](https://jsonschema.net/#/editor) editor to help create JSON schema from your object.
- [JSON Schema Validator](http://www.jsonschemavalidator.net/) An online, interactive JSON Schema validator.

## Tools

There are also a number of npm tools to help you with your extension package development:

- [Data Collection Extension Scaffold Tool](https://www.npmjs.com/package/@adobe/reactor-scaffold) helps you easily create a starter project on your local machine.
- [Data Collection Extension Sandbox](https://www.npmjs.com/package/@adobe/reactor-sandbox) helps you validate your extension views and modules on your local machine.
- [Data Collection Extension Packager](https://www.npmjs.com/package/@adobe/reactor-packager) is a command-line utility for packaging a Data Collection extension into a zip file.
- [Data Collection Extension Uploader](https://www.npmjs.com/package/@adobe/reactor-uploader) is an interactive command line tool to help you input your technical account credentials and upload your extension package to tags in Adobe Experience Platform.
- [Data Collection Extension Releaser](https://www.npmjs.com/package/@adobe/reactor-releaser) is an interactive command line tool to help you release your extension to private availability.

## Example extensions

There are example extensions on GitHub you can review or use as starter projects:

- [Hello World example extension](https://github.com/adobe/reactor-helloworld-extension)
- [Facebook example extension](https://github.com/Adobe-Marketing-Cloud-Activation/extension-facebookpixel)
- [Typekit example extension](https://github.com/jeffchasin/extension-typekit)
- [Pinterest example extension](https://github.com/jeffchasin/extension-pinterest)

## Slack workspace

There is a Slack community workspace where extension authors can support each other. You can request access at [http://join.launchdevelopers.chat](http://join.launchdevelopers.chat).

**Please note**: while there are members of the tags team in this Slack workspace, it is a community resource not sponsored by or moderated by Adobe.
