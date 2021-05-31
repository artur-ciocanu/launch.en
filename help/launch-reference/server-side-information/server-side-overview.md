---
title: Adobe Experience Platform Launch Server Side Overview
description: Learn about Adobe Experience Platform Launch Server Side, which allows you to use the Platform Edge Network to execute tasks without changing your client-side implementation.
exl-id: a349ee6c-9854-43d0-adca-2d8f086b63b8
---
# Adobe Experience Platform Launch Server Side overview

>**Note**: Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../../launch-name-updates) for a consolidated reference of the terminology changes.

Adobe Experience Platform Launch Server Side decreases web page and app weight by using Adobe Experience Platform Edge Network to execute tasks normally done on the client. Platform Launch Server Side rules can transform and send data to new destinations without changing client-side implementations.

Platform Launch Server Side, combined with the Adobe Experience Platform Web and Mobile SDKs, makes it possible to:

* Make a single call from the page that contains a payload of data and then federate this data server-side to reduce client-side network traffic and deliver a faster experience for customers.
* Decrease the amount of time it takes for web pages to load so your site conforms to industry best practices around performance.
* Increase transparency and control over which types of data are sent where, across all client-side properties.
* Create a server-side rule to send previously tracked data to a new destination.

## Improved performance

In an increasingly competitive environment, businesses must prioritize performance to maintain and expand market share. Platform Launch Server Side improves website and app performance across mobile, IoT, and OTT devices. Website conversion rates can increase due to faster load times, mobile apps don't drain batteries as quickly, and OTT apps feel as responsive as those same apps running on mobile devices. As performance increases, it's also common for conversion rates to increase.

## Better data governance

As the technology stack grows and data is sent to more and more destinations, the challenge to control what data is sent where becomes more difficult. The normalization of regulations like GDPR and CCPA force companies to exert more control over a data problem that’s increasingly becoming harder.

Platform Launch Server Side helps marketing teams grow their business while controlling data. It decreases the number of client-side technologies that marketers need to use to reach their target market and send data to non-Adobe destinations. This makes it easier for implementation teams to manage the data flowing from the client to various destinations.  

## Differences between Platform Launch Server Side and Platform Launch Client Side

It is important to note the following differences between [!DNL Platform Launch] Server Side and [!DNL Platform Launch] Client Side:

* Data element tokenization

    * Client Side: In a rule, data elements are tokenized with a `%` at the beginning and end of the data element name. For example, `%viewportHeight%`.

    * Server Side: In a rule, data elements are tokenized with `{{` at the beginning and `}}` at the end of the data element name. For example, `{{viewportHeight}}`.

* How data is referenced
    
    To reference data from the Edge network, the data element path must be `arc.event._<element>_`.
    
    `arc` stands for Adobe Response Context.

    For example: `arc.event.xdm.web.webPageDetails.URL`
    
    >[!IMPORTANT]
    >
    >If this path in specified incorrectly, data is not collected.
    

* Sequence of rule actions

    In the Action section of a rule, server-side rules are always executed sequentially. Make sure the order of actions is correct when you save a rule. This execution sequence cannot be chosen like it can on Platform Launch Client Side.

* Custom code JavaScript versions

    Platform Launch Client Side uses JavaScript version es5. Platform Launch Server Side uses version es6.

<!--doc Adobe Cloud Connector extension, get from Jon-->
