---
title: Notes
description: Learn how to textual annotations to certain resources in Adobe Experience Platform Launch.
exl-id: 47bc15ea-8bff-42fc-8011-5498ab11e400
---
# Notes

>[!NOTE]
>
>Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../../launch-name-updates) for a consolidated reference of the terminology changes.

Notes are textual annotations that you can add to certain Adobe Experience Platform Launch resources.  Notes can be attached to the following resources:

* Extensions
* Data elements
* Rules
* Rule components
* Libraries
* Properties

Notes can contain up to 512 Unicode characters.  

Notes are comments that have no impact on the behavior of the resources they are attached to.  They are not included in built libraries.  You might use notes to:

* Provide background information on a resource
* Function as a to-do list for future enhancements
* Pass along resource usage advice to other users
* Give instructions to other team members
* Record historical context
* Remind yourself what a resource does, why it is built the way it is, or where it gets used

## Create a note

Noteable resources display a narrow rail on the right-hand side of the screen.  The rail includes an icon for notes.  This icon displays the current number of notes attached to the resource.

Select **[!UICONTROL Notes]** to expand the right rail and display the notes, with the most recent notes at the top.  To add a new note, enter your note text in the box at the top and select **[!UICONTROL Add Note]**.

## Other

* Notes in Platform Launch match the behavior of notes in DTM, in that they are immutable and cannot be edited or deleted.
* When viewing older revisions of a resource, only the notes that were created prior to that revision's `created_at` date are displayed.
* When you delete a resource, all notes attached to the resource are also deleted.
