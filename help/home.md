---
title: Tags Overview
description: Tags in Adobe Experience Platform data collection are the next generation of tag management capabilities from Adobe. Platform data collection gives customers a simple way to deploy and manage all of the analytics, marketing, and advertising tags necessary to power relevant customer experiences.
exl-id: 93ce11e3-5c88-4822-b5df-e32839f29f34
---
# Adobe Experience Platform tags overview

>[!NOTE]
>
>Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](./launch-term-updates.md) for a consolidated reference of the terminology changes.

Adobe Experience Platform tags are the next generation of tag management capabilities from [!DNL Adobe]. Data collection gives customers a simple way to deploy and manage all of the analytics, marketing, and advertising tags necessary to power relevant customer experiences.

Adobe Experience Platform tags empower anyone to build and maintain their own integrations, called _extensions_. These extensions are available to [!DNL Adobe Experience Cloud] customers in an app-store experience so they can quickly install, configure, and deploy their tags.

Tags are offered to [!DNL Adobe Experience Cloud] customers as an included, value-add feature. Tags are an entirely new product with a new code base, designed to replace the previous [!DNL Dynamic Tag Management (DTM)] service. However, [!DNL DTM] will continue to be supported for the foreseeable future. [!DNL Adobe] will continue to fix any significant bugs and ensure consistent performance. At this time, no major feature enhancements are planned for legacy [!DNL DTM].

## Key benefits

- Faster time to value.
- Trustworthy data through a centralized collection, organization, and delivery using data elements.
- Compelling experiences through the integration of data and marketing technology using rule builder.

## Key features

### Extensions

An extension is a package of code (JavaScript, HTML, and CSS) that extends the tags UI and client functionality. Build, manage, and update your integrations using a virtually self-service interface. You can think of extensions as apps you use to achieve your tasks.

### Extension catalog

Browse, configure, and deploy marketing/advertising tools built and maintained by independent software vendors.

### Rule builder

Create robust rules that combine multiple events, sequenced in the way that you determine using if/then logic with conditions and exceptions. Rules provide options for:

- Events
- Conditions
- Exceptions
- Actions

The rule builder includes real-time error checking and syntax highlighting for your custom code.

When the criteria outlined in your rules are met and conditions are satisfied, the actions you define are executed in order.

### Data elements

Collect, organize, and deliver data across web-based marketing and advertising technology.

### Enterprise publishing

The publishing process enables teams to publish code to pages. Different people can create an implementation, approve it, and publish it on your pages.

- Changes to your code are encapsulated within the libraries you define.
- You specify where and when you want your code deployed.
- Multiple libraries can be built in parallel by different teams.
- Unlimited development environments.
- A deliberate, permission-based process for merging libraries together.

### Open APIs

Automate implementations of individual technologies or a group of technologies.

- Tags interacts with the Reactor API.
- Deployments can be automated through APIs.
- Integrate the tags APIs with your own internal systems.
- You can build your own user interface if desired.

### Light, modular container tag

The tags container tag is 60% lighter than [!DNL DTM]. The content of your container is minified, including your custom code. Everything is modular. If you don't need an item, it is not included in your library. The result is an implementation that is fast and compact. See [Minification](/help/launch-reference/publishing/builds.md).

## Other highlights

Adobe Experience Platform tags provide several improvements over similar systems, including:

- No use of `document.write ()` where Chrome doesn't allow it.
- The Page Top and Page Bottom rules are bundled into the main library to minimize unnecessary HTTP calls.
- Custom action scripts within a rule can be loaded in parallel, but are executed sequentially.
- If you avoid Page Top and Page Bottom rules, the code is mostly asynchronous, with a path to getting fully async.

## Requirements

Adobe Experience Platform tags require the following:

- You must be an [!DNL Adobe Experience Cloud] customer.
- You must deploy the embed code, or [!DNL DTM] embed code on your web pages.
