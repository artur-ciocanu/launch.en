---
title: Release Notes
description: The latest release notes for Adobe Experience Platform Launch.
exl-id: 7d76f141-9732-4f68-8a50-9d43b3f4444c
---
# Release notes

=======
## May 10th, 2021

**Simplified Publishing** - Building to the staging environment is no longer required.  If you have the appropriate rights, you can skip the Submitted state entirely and publish directly from Development as long as you’ve had a successful build and there are no other libraries upstream.

## April 22nd, 2021

**Adobe Experience Platform Data Collection** - Sending data to Adobe is not just about deploying tags to your site or configuration to your app.  Usage of the Experience Platform SDKs and the Edge Network require access to other Platform capabilities.  This used to require logging into a few different tools, but now they are together in one place.

Platform Data Collection consists of six capabilities, and your newly streamlined navigation will only contain the items that your company and user account have access to.  Some of the capability names have also been updated to match Experience Platform's naming patterns.

* Client (formerly accessed as Client Side)
* Datastreams (formerly accessed as Edge Configurations)
* Server (formerly accessed as Server Side)
* App Configurations
* Schemas
* Identities

Look forward to more updates as Experience Platform and Data Collection continue to evolve.

## February 18th, 2021

* Updated the Adobe Experience Platform Launch UI to react-spectrum v3
* Updated extension cards to the latest Spectrum patterns
* Increased the size of name fields throughout the app

## January 13th, 2021

**General Availability: Launch Server Side** Send event-level data to the Adobe Experience Platform Edge Network then use Launch Server Side to transform, enrich, and send that data to a non-Adobe endpoint using Adobe's servers, not the client, with low latency.

See [Launch Server Side overview](https://experienceleague.adobe.com/docs/launch/using/server-side-info/server-side-overview.html?lang=en#server-side-info) and [Getting started with Experience Platform Launch Server Side](https://experienceleague.adobe.com/docs/launch/using/server-side-info/server-side-getting-started.html?lang=en#server-side-info) for more information.
