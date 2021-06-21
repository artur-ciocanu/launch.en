---
title: Getting started with Adobe Experience Platform Launch Server Side
description: Follow this step-by-step tutorial to get started using Adobe Experience Platform Launch Server Side.
exl-id: b565af18-2208-4c36-9d0f-1939b4c623aa
---
# Getting started with Experience Platform Launch Server Side

>[!NOTE]
>
>Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../../launch-term-updates.md) for a consolidated reference of the terminology changes.

To use Adobe Experience Platform Launch Server Side, data must be sent to Adobe Experience Platform Edge Network using one or more of three options:

* Adobe Experience Platform Web SDK
* Adobe Experience Platform Mobile SDK (coming in H2 2021)
* Server-to-Server API (coming in H2 2021)

>[!NOTE]
>The Platform Web SDK and Platform Mobile SDK do not require deployment through Platform Launch Client Side. However, using Platform Launch Client Side to deploy these SDKs is the recommended approach.

After you send data to Edge network, you can toggle on Adobe solutions to send data there. To send data to a non-Adobe solution, set that up in Platform Launch Server Side.

## Prerequisites

* Adobe Experience Platform Collection Enterprise (Contact your account manager for pricing)
* Adobe Experience Platform Launch Server Side
* Adobe Experience Platform Web or Mobile SDK, configured to send data to Edge Network
* Map data to Experience Data Model (XDM) (This mapping can be done Platform Launch Client Side)

## Create an XDM schema

In Adobe Experience Platform, create your schema.

1. Create a schema by selecting **[!UICONTROL Schemas]**>**[!UICONTROL Create Schema]** and choosing the **[!UICONTROL XDM ExperienceEvent]** option.

1. Give the schema a name and short description.

1. You can add the “ExperienceEvent web details” mixin by selecting **[!UICONTROL Add]** next to **[!UICONTROL Mixins]**. 

    >[!NOTE]
    >
    >Multiple mixins can be added, if desired.

1. Save the schema and note the name that you gave it.

For more information about schemas, see [Experience Data Model (XDM) System Help](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html).

## Create Platform Launch Server Side property

In Platform Launch, create a property of type "Edge."

1. Select **[!UICONTROL New Property]**. 

1. Name the property. 

1. Choose the “Edge” platform type.

1. Select **[!UICONTROL Save]**.

After you create the property, go to the **[!UICONTROL Environments]** tab for the new property and make
note of the environment IDs. You can copy the Environment ID from the **[!UICONTROL Environments]** tab to paste it when
creating an Edge configuration, if the Adobe Org used in Edge Configuration differs from the Adobe Org used
in Platform Launch Server Side. Otherwise, you can select the environment from a drop-down menu.

## Create Edge Configuration

In Adobe Experience Platform Edge Configuration, create your edge configuration. Use the Environment ID generated when you created the Platform Launch Server Side property.

1. Open the Adobe Experience Platform Edge Configuration interface through Platform Launch, from the link in the left rail.

1. Select **[!UICONTROL New Edge Configuration]**.

1. Name the configuration and provide an optional description. 
    The description helps to identify configurations in a list of several configurations. 

1. Select **[!UICONTROL Save]**.



## Enable Platform Launch Server Side

Next, configure Edge Network to send data to Platform Launch Server Side, and to other Adobe products.

1. In the Edge Configuration UI, select the property you created.

1. Select the Development, Production, or Staging environment.

    Or, to send data to a Platform Launch Server Side environment outside the Adobe org, select **[!UICONTROL Switch to Advanced Mode] and paste in an ID. The ID is provided when you create a Server Side property.

1. Toggle on the necessary tools and configure as required.

    * Adobe Analytics requires a report suite ID.

    * Platform Launch Server Side requires a property ID and environment ID, which is the publish path for the Platform Launch Server Side property.

After configuring, make note of the Environment IDs for the new property.

## Configure the Platform Web SDK extension for Platform Launch Client Side to send data to the Edge configuration that you created

In Platform Launch Client Side, create your property, then use the Adobe Experience Platform Web SDK extension to configure it.

1. Name the property.

    You can have multiple instances of Alloy. For example, you might have different pre- and post-paywall tracking properties.

1. Select the Org ID.

1. Select the Edge Domain.

See the [Web SDK extension documentation](https://experienceleague.adobe.com/docs/launch/using/extensions-ref/adobe-extension/aep-extension/overview.html) for more configuration options.

## Create a Platform Launch Client Side rule to send data to Platform Web SDK

After the above is in place, build data definitions, rules, and so on, that use Platform Launch Server Side and Platform Launch Client Side, but that need only a single request from the page.

Create a page load rule using the Platform Web SDK extension and the “Send Event” action type:

1. Open the **[!UICONTROL Rules]** tab, then select **[!UICONTROL Create New Rule]**.

1. Name the rule.

1. Select **[!UICONTROL Events Add]**.

1. Add an event by choosing an extension and one of the event types available for that extension, then configure the settings for the event. For example, select **[!UICONTROL Core - Window Loaded]**.

1. Add an action using the Platform Web SDK extension. Select **[!UICONTROL Send Event]** from the **[!UICONTROL Action Type]** list, select the desired Instance (Alloy instance configured earlier), and then select a data element to add to the XDM Data block within the Alloy hit.

1. Leave the rest of the settings as default for this example, and select **[!UICONTROL Save]**.

For another example, you might create a rule that sends the data layer to Edge if the user hovers over a specified button.

## Summary

With the following in place, you can now create Platform Launch Server Side rules to forward data to
non-Adobe destinations.

* Experience Data Model schema (Note the name that you gave it.)
* Platform Launch Server Side property (Keep track of the property ID and environment IDs.)
* Adobe Experience Platform Edge Configuration (Note the environment ID, not to be confused with the environment ID from Platform Launch Server Side.)
* Platform Launch Client Side property
