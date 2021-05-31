---
title: FAQ
description: Get answers to frequently asked questions about Adobe Experience Platform Launch.
exl-id: 1192c0cd-fa2d-4c82-978c-af75a70d060b
---
# Adobe Experience Platform Launch FAQ

>[!NOTE]
>
>Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../../launch-name-updates) for a consolidated reference of the terminology changes.

This document provides answers to frequently asked questions about Adobe Experience Platform Launch.

## What is Platform Launch?

[!DNL Platform Launch] is the next-generation of the [!DNL Adobe] tag-management capability, built into the [!DNL Adobe Experience Platform]. [!DNL Platform Launch] enables clients to:

- Deploy client-side web products using integrations called _extensions_
- Dynamically deliver configuration to update client implementations in native mobile applications
- Consistently capture, define, manage, and share data between marketing and advertising products from other vendors and from [!DNL Adobe]

[!DNL Platform Launch] is an advanced code and configuration delivery system that evaluates conditions and executes actions to efficiently and effectively deploy client-side libraries and products. It also provides a highly scalable approach to managing and building integrations and has a robust set of APIs for programmatic interaction.

## Is Platform Launch just an updated DTM?

No. [!DNL Platform Launch] is a tag manager, but it is not an update to DTM. [!DNL Platform Launch] is an entirely new product with a new code base. It has been redesigned from scratch using modern front-end development practices and an API-first approach. Everything is built on a robust set of APIs, which makes the system very powerful, flexible, and customizable.

## Will the current DTM product remain available?

For now, yes, but not indefinitely. DTM has a [defined sunset plan](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/dtm-plans-for-a-sunset/ba-p/331077) with specific milestones that will progressively limit its functionality. The next Milestone is set for October of 2020 when DTM properties will become read-only. At this time, no major feature enhancements are planned for legacy [!DNL DTM].

A migration assistant is available to copy properties from DTM into [!DNL Platform Launch] , you can read more about that [here](https://docs.adobe.com/content/help/en/launch/using/reference/upgrade/overview.html) and [here](https://docs.adobe.com/content/help/en/core-services-learn/tutorials/launch-web/migrate-from-dynamic-tag-manager-to-launch.html).

## How much does Platform Launch cost?

There is no additional charge for [!DNL Platform Launch]. It is available for any [!DNL Adobe Experience Cloud] customer.

## Do I have to change the embed codes in my current DTM implementation?

No, you don't have to change your production embed codes if you're currently using the existing (legacy) [!DNL DTM] system. You can continue to work in your current [!DNL DTM] Company and Web Properties without worrying about changing that embed code. For more details, see the [Platform Launch help docs](https://docs.adobe.com/content/help/en/launch/using/reference/upgrade/overview.html), and this [blog post](https://medium.com/launch-by-adobe/migrating-from-dtm-to-launch-57548251a86d).

## I heard there are plug-ins now. What's that about?

[!DNL Platform Launch] is built into the [!DNL Adobe Experience Platform] and it is fully extensible. Customers, [!DNL Adobe] Partners, agencies, and marketing or advertising technology vendors can build [!DNL Platform Launch] extensions that add new functionality or modify existing functionality. The system allows partners and clients to build, manage, and update their own integrations. This is just one way [!DNL Adobe] is opening up the [!DNL Adobe Experience Platform] so customers and partners can build products and businesses on it. This helps everyone connect Adobe technology to the marketing and advertising technologies from other vendors with greater ease.

## Will all third-party extensions be available right away?

Extensions are already available for [!DNL Adobe] solutions and a large and growing number independent analytics, marketing, advertising, and consent vendors and technologies. We continue to work with our partners to expand the ecosystem. Because extensions can be built, managed, and updated by the technology owners, customers don't have to wait for [!DNL Adobe] engineering to build them.

## When can clients or partners build extensions?

[!DNL Platform Launch] has opened its virtually self-service portal, which extension developers can use to build their own integrations with the [!DNL Adobe Cloud Platform].

We have many customers who also choose to build their own private extensions for use only within their own companies using the same extension development methods.

## Does Platform Launch meet my company's security standards?

[!DNL Platform Launch] is SOC-2 and Gramm-Leach-Bliley Act ready. [!DNL Platform Launch] also offers the capability of being self-hosted. JavaScript libraries and mobile configurations can be served from your own servers, or the CDN of your choice. For I.T. and security teams, this gives you the ability to run automated testing, to check the files into your own version control system, and to fully comply with any internal production migration processes, security-related or otherwise.

## When can I move to Platform Launch?

Now! You should move to Platform Launch now. The migration process makes easy to copy your DTM properties into [!DNL Platform Launch]. We recommend extensive testing, but we've automated as much as we can (no on-page embed code changes, and automated migration of rules and data elements).

## Which capabilities exist in Platform Launch that don't exist in legacy DTM?

[!DNL Platform Launch] many major capabilities that aren't comparable to legacy [!DNL DTM]:

- Deploy non-[!DNL Adobe] client-side browser technologies quickly and easily

  Using extensions, clients and partners can easily control in-browser technologies in the interface, without managing custom code.

- Enterprise-grade publishing

  Compartmentalize and control each piece of your libraries to deploy precisely what you need, where you need it, and when you need it.

- Robust approval workflows

  Flexible approval workflows allow custom processes to match your existing internal approval processes.

- Granular rights management

  Administrators will designate which extensions users can, and can't use. They will also control which areas within [!DNL Platform Launch] are accessible to certain users.

- APIs

  Many customers different integrations with [!DNL Platform Launch] using the APIs. Some have hooked [!DNL Platform Launch] into into their site deployment pipelines, others have made proeprty cloning tools, while others have made applications to download local copies of their properties where they can make changes and sync them back to [!DNL Platform Launch].

## Does Platform Launch support single page apps and my favorite framework?

Yes. [!DNL Platform Launch] has capabilities to give users and extension developers flexibility in collecting, managing, and distributing data within single page application experiences or Ajax-heavy pages or sites. This applies regardless of your development framework preferences, whether that's Angular, React.js, Ember, Meteor, etc.

## Does Platform Launch support dynamic data layers?

Yes. [!DNL Platform Launch] includes an extension that specializes in listening for changes in dynamic data layers.

## Which event types does Platform Launch support?

Event types are available through extensions. The pre-loaded [!DNL DTM] extension includes 30 built-in event types. Other extensions could add additional event types. For example, the YouTube extension includes four video event types: play, pause, end, and time played. Through extensions, [!DNL Platform Launch] can support any other browser event types or synthetic event types, such as specific visitor activity sequences.

## Will Platform Launch speed up (or slow down) my web site?

[!DNL Platform Launch] is designed to deliver and run marketing and advertising technologies on your web site as efficiently as possible using today's best practices. When used properly, [!DNL Platform Launch] has proven to improve performance of web sites over alternative methods of providing similar functionality.

## Which browsers does Platform Launch support?

Browser support in the [!DNL Platform Launch] client-side libraries:

- [!DNL Chrome] (latest)
- [!DNL Safari] (latest)
- [!DNL Firefox] (latest)
- [!DNL Microsoft Edge] (latest)
- [!DNL Internet Explorer] (10 and above)
- [!DNL iOS Safari] (latest)
- [!DNL Android Chrome] (latest)

Browser support in the [!DNL Platform Launch] application interface:

- [!DNL Chrome] (latest)
- [!DNL Safari] (latest)
- [!DNL Firefox] (latest)
- [!DNL Microsoft Edge] (latest)

Legacy [!DNL DTM] supported older versions of [!DNL Internet Explorer], but over the last few years, the percentage of overall web users with older, outdated browsers has dropped to a small segment for our clients. Most [!DNL Adobe] clients now leverage more modern web platform features in current browsers and create better user experiences, including single page applications and interactive Ajax-heavy web sites and pages. As most clients move to more modern approaches with their sites, they demand a solution like [!DNL Platform Launch] that enables those approaches.

## Does Platform Launch work on native mobile apps?

Yes! [!DNL Platform Launch] now supports mobile properties and configuration for the new [!DNL Adobe Experience Platform] [Mobile SDKs](https://sdkdocs.com) to implement data collection and delivery in a native mobile app environment. Please visit [documentation](https://sdkdocs.com) to learn more.

## What if I have other questions?

If you have other questions, please ask in the [!DNL Adobe] Community on the main [!DNL Platform Launch] page located at [https://adobe.com/go/launchme](https://adobe.com/go/launchme).

[!DNL Platform Launch] is just one example of where our platform is headed: more open, more integrated and as always dedicated to customer success.
