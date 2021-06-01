---
title: Quickstart Guide
description: Learn how to quickly get up and running with Adobe Experience Platform Launch.
exl-id: 12be4e94-1838-4aea-92a1-4a4862d3cb1f
---
# Quickstart guide

>[!NOTE]
>
>Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../launch-term-updates.md) for a consolidated reference of the terminology changes.

[!DNL Adobe Experience Platform Launch] is the next-generation of [!DNL Adobe's] tag management technology, built on the [!DNL Adobe Experience Platform]. It is built from the ground up to support an open and sustainable ecosystem where anyone can build their own integrations that [!DNL Adobe] customers can deploy to their sites. It is an API first application so anything you can do through the UI you can also do programmatically through an API.

The basic [!DNL Platform Launch] workflow:

1. Set up groups and users.
1. Log in.
1. Create a property.
1. Install extensions.
1. Create data elements and rules.
1. Test in your dev environment.
1. Promote to production.

For an introductory video, see [Introduction to Experience Platform Launch](videos.md).

## 1. Set up groups and users

[!DNL Platform Launch] is fully integrated with your [!DNL Adobe] ID. User permissions are managed through the Admin Console with other Adobe products and solutions from the [!DNL Creative Cloud], [!DNL Document Cloud], and [!DNL Experience Cloud].

Unlike [!DNL DTM], [!DNL Platform Launch] has rights-based user management. ([!DNL DTM] was role-based.) This means that instead of getting a role which implies a certain set of rights, individual rights must be granted explicitly. These rights are assigned to groups, then users are added to the appropriate groups in order to gain access. Even if your company has access to [!DNL Platform Launch], individual users cannot do anything until an Org Administrator explicitly grants them some rights.

For detailed instructions on how to create groups and add users for [!DNL Platform Launch], see [Users](../launch-reference/administration/user-permissions.md).

## 2. Log in

After [!DNL Platform Launch] rights have been added to your [!DNL Adobe] ID, you need to log in to [!DNL Platform Launch]. You can do this by navigating directly to [https://launch.adobe.com](https://launch.adobe.com) or by logging in to the [Experience Cloud (https://experiencecloud.adobe.com)](https://experiencecloud.adobe.com), navigating to the [!UICONTROL Activation] page, and selecting **[!UICONTROL Launch]**.

## 3. Create a property 

Once you're in [!DNL Platform Launch], the first thing to do is create a property. A property is basically a container that you fill with extensions, rules, data elements, and libraries as you deploy tags to your site. Many people create a property for each website (or group of closely related sites) where they want to deploy the same set of tags.

For more about creating properties, see [Create a property](../launch-reference/administration/companies-and-properties.md).

## 4. Install extensions

An extension is an integration built by [!DNL Adobe] or an [!DNL Adobe] partner that adds new and endless options for the tags that you can deploy to your sites. If you think of [!DNL Platform Launch] as an operating system, extensions are the apps that you install so [!DNL Platform Launch] can do the things you need it to do.

All new properties come with the [Core extension](../extension-reference/web/core-extension/overview.md) installed. Mobile properties come with additional extensions. The Core extension is built by the [!DNL Platform Launch] team to provide a robust default set of data element types for your data layer and event types for your rules. Most actions you will want to perform (get an ECID, send [!DNL Adobe Analytics] beacons, load the [!DNL Target] global mbox, etc) will come from extensions that you install from the catalog.

What makes [!DNL Platform Launch] truly unique among tag management systems is that these extensions can be built by anyone. Do you need to drop a Facebook remarketing pixel on your site? Check out the extension that Facebook built. Do you want the same for Twitter or Linked In? Use those extensions. Do you need to run a survey? Look at Question Pro or Foresee. Do you need to manage privacy and consent from your end users to help out with [!DNL GDPR]? Take a good look at Evidon and Trust Arc. Would you like to see really granular insight into the behavior of individual users on your site? Maybe take a look at Clicktale. For more information, see [Add a new extension](../launch-reference/managing-resources/extensions/overview.md#add-a-new-extension).

## 5. Create data elements and rules

**Data elements** are pointers to the information that you want to collect and send to different places on your page:

* A defined data layer in JSON
* DOM elements
* Cookies
* Session and local storage
* Just about everything else

After the data element is defined, you can use the element anywhere throughout [!DNL Platform Launch]  for any extension. (See [Data Elements](../launch-reference/managing-resources/data-elements.md).)

**Rules** are at the logical core of your implementation and control the what, when, where, and how of all the tags on your site. Define an event, set conditions and exceptions, then define the actions and order. Finally, publish your changes to see the results. For more information, see [Rules](../launch-reference/managing-resources/rules.md).

## 6. Test in your Dev environment 

### Libraries and builds

Nothing in [!DNL Platform Launch] is published automatically. Each set of changes you make is encapsulated into a [library](../launch-reference/publishing/libraries.md). Each library you create automatically inherits anything upstream (published, approved, or submitted) as a baseline, so all you need to do is define the changes you'd like to make. This library serves as the blueprint for a [build](../launch-reference/publishing/builds.md). A build is the actual set of JavaScript files that are deployed and used.

To make sense of that process, there are some relationships between [!DNL Platform Launch], your web page, and your hosting location that you need to understand.

![](/help/assets/loop.png)

1. [!DNL Platform Launch]  publishes a build to your host server.

   As mentioned above, a build is the actual JavaScript file(s) that [!DNL Platform Launch] produces. This relationship between [!DNL Platform Launch] and your host location is defined by a host. Read more about hosts below.

1. [!DNL Platform Launch] provides an embed code `<script>` tag that goes onto your site.

   When you create an environment and attach a host, the environment provides this `<script>` tag for you to put on your pages.

1. When a user browses your site, the Embed Code `<script>` tag retrieves the build from your host server and performs your defined actions within the browser.

### Hosts

An host is a connection between [!DNL Platform Launch] and your hosting location. [!DNL Platform Launch] currently supports an [!DNL Akamai] host and an SFTP host. Whenever you produce a build, [!DNL Platform Launch] connects to the server defined by your host and delivers the build.

If you want to self-host, you can have [!DNL Platform Launch] push directly to your servers through SFTP or you can push it to [!DNL Akamai] and download it (using your environment's Archive option).

For more information, see [Hosts](../launch-reference/publishing/hosts/hosts-overview.md).

### Environments

Each library is created inside an environment. An environment defines how you want your build to look when it is published. You can specify:

* **Host:** Each environment needs a host which determines where [!DNL Platform Launch] will push any builds created in this environment
* **Archive:** The default is to deploy your build as a minified .js file (or if you're using custom code, multiple files which reference each other). You can have wrap all these together into a zip file and encrypt it.

After you have saved your environment, it generates the embed code which you can copy and paste into your website. Note that the embed code will not work until you have actually created a library and produced a build. For more information, see [Environments](../launch-reference/publishing/environments.md).

### Publish a build to Dev

Now that you understand the basic components, the publishing process should make more sense. You need to:

1. Create an host.
1. Create a dev environment using the host you created.
1. Deploy the embed code from your dev environment to your dev test site.
1. Create a library and assign it to the dev environment you created.
1. Build your library.

## 7. Promote to production 

After you've tested your build in your dev environment, the promotion process is pretty straightforward. Before you try it out, make sure to create your stage and production environments and put the embed codes in the necessary places. (You can reuse existing hosts.)

Promoting a library all the way through to production typically requires coordination among different people with the appropriate rights.

* A Developer (someone with the Develop right) submits the library, which moves the library to the Submitted state.
* An Approver (someone with the Approve right) can build the library to the stage environment and can approve it after testing. This moves the library to the approved state. Only one library can be submitted and approved at a time.
* A Publisher (someone with the Publish right) can build the library to the production environment.

You can assign all these rights to a single person.

For more information about the different states and options available during the publishing process, see [Approval Workflow](../launch-reference/publishing/publishing-flow.md).

## Additional resources

To learn more about [!DNL Platform Launch], refer to these resources:

[https://forums.adobe.com/community/experience-cloud/platform/launchAsk](https://forums.adobe.com/community/experience-cloud/platform/launchAsk) and answer questions, submit ideas, vote on the ideas of others. Log in with your [!DNL Adobe] ID.

* **[Platform Launch Community](https://forums.adobe.com/community/experience-cloud/platform/launch)**: Ask and answer questions, submit ideas, vote on the ideas of others. Log in with your [!DNL Adobe] ID.
* **[Platform Launch Webinars](https://adobe.com/go/launchme)**: Sign up for upcoming webinars and watch recordings of past webinars.
* **[Developer Docs](https://developer.adobelaunch.com/)**: Get involved with the [!DNL Platform Launch] developer community to build extensions or use the [!DNL Platform Launch] APIs
* **[Videos](https://docs.adobe.com/content/help/en/core-services-learn/tutorials/overview.html)**

  These videos introduce you to [!DNL Platform Launch] concepts and tasks.
