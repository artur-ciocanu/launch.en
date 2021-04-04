---
title: Libraries
description: Learn about the concept of libraries and how they function within Adobe Experience Platform Launch.
exl-id: 9be19d44-bece-4a1f-8531-726b8474c220
---
# Libraries

A library is a set of instructions for how extensions, data elements, and rules interact with one another after they are deployed.

When creating a library, you specify the changes you want to make to your library.

At build time, these changes are combined with everything that has been submitted, approved, or published in previous libraries.

Libraries contain the addition or removal of:

* Rules
* Elements
* Extension configuration

Libraries must be assigned to an environment before they can be compiled into a build.

Libraries are approved or rejected as a whole. You cannot approve or reject individual items within a library.

A library moves between several environments as it makes its way through the publishing workflow.

## Create a library {#create-a-library}

1. Open the [!UICONTROL Publishing] tab.

   The [!UICONTROL Publishing] page lists the Dev libraries and provides the means to submit them for approval, move them to staging, or publish them to production.

1. Select **[!UICONTROL Add New Library]**.

   ![](/help/assets/library-create.jpg)

1. Name the library.
1. Assign the library to a Dev environment.
1. Add a change to the library.
   To add an item, select **[!UICONTROL Add a Change]**, then choose the items you want to add. Any item that has been edited or deleted is available to add to the chosen library.

   ![](/help/assets/library-add-change.jpg)

   You can add the following to your library:

   * Rules
   * Data elements
   * Extension configurations

1. To add any resources that have changed, select **[!UICONTROL Add All Changed Resources]**.
1. Select **[!UICONTROL Save]** or **[!UICONTROL Save and Build for Development]**.

   Deploying compiles a build and deploys it to the assigned environment.

Once a library is created, use the drop down menu for that library to select one of the following options:

* Edit

  Change the library configuration.

* Build for Development

  Compiles a build and deploy it to the assigned environment.

* Submit for Approval

  Make the library available for an Approver to move it to the next step in the publishing process

* Delete

  Remove that library from the publishing process.

![](/help/assets/library-menu.png)

## Add to a library {#add-to-a-library}

1. Install the [extensions](../managing-resources/extensions/overview.md) you want to add.
1. Create the [data elements](../managing-resources/data-elements.md) and rules you want to add.
1. Open the [!UICONTROL Publishing] tab.
1. Select the [library](libraries.md) you want to change, then select **[!UICONTROL Edit]**.
1. Use the rules, data elements, and extensions buttons to select the items you want to add to the library.
1. Save.

Changes to the library are shown in the Library Contents change log.

>[!NOTE]
>
>Data elements can depend upon extensions. Rules can depend on both data elements and extensions. If you do not include all the necessary components in your library, the build will fail at build time and you'll need to add the necessary components before you complete a successful build. A future release will check dependencies when making changes to a library.

## Remove from a library

To remove something from a library, you must deactivate it and then publish the deactivated state.

1. Disable the extensions you want to remove, along with any data elements and rules that depend on those extensions.
1. Disable the data elements and rules you want to remove.
1. Open the [!UICONTROL Publishing] tab.
1. Select the library you want to change.
1. Use the rules, data elements, and extensions buttons to select the disabled items you want to remove from the library.
1. Save.

## Manage library changes

1. Choose a library and select **[!UICONTROL Edit]** to view library changes. All changes are shown in the [!UICONTROL Library Contents] list.

   ![](/help/assets/library-contents.jpg)

1. Select a change to view and select a revision.

   ![](/help/assets/library-contents-revision.jpg)

1. Select whether to show all items or changed items.
1. Select the revision, then select **[!UICONTROL Select Revision]**.
1. Select either **[!UICONTROL Add a Change]** or **[!UICONTROL Add All Changed Resources]**.

## Active Library {#active-library}

Libraries encapsulate a set of changes you'd like to make to your deployed code. Active Library makes this easier, allowing you to rapidly iterate through changes and see the impact.

You can save new and existing extensions, rules, and data elements directly to the library you're working on and, if desired, immediately kick off a build. You can also create a new library from the [!UICONTROL Active Library] drop down.

1. [Create a new library](libraries.md#create-a-library).
1. Go to [Rules](../managing-resources/rules.md), [Data Elements](../managing-resources/data-elements.md), or [Extensions](../managing-resources/extensions/overview.md).
1. Select your Active Library.
1. Make your changes, then save and build the library.
1. Test your changes, and repeat these steps as needed.
