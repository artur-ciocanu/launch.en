---
title: User Permissions
description: Learn about the different available permissions for Adobe Experience Platform Launch users.
exl-id: 43ed8522-452a-47fe-b316-564f80b012af
---
# User permissions

## Permission types

To work in [!DNL Adobe Experience Platform Launch], there are two user permissions to understand:

* **Experience Cloud Permissions:** Found in the Admin Console at the company level, [!DNL Experience Cloud] permissions govern who can control group permissions and group membership for all [!DNL Experience Cloud] products.
* **Platform Launch Permissions:** The permissions for [!DNL Platform Launch], one of the [!DNL Experience Cloud] products, are found in the Admin Console at the Product Profile level. [!DNL Platform Launch] permissions govern which users can actually perform certain actions when logged into [!DNL Platform Launch].

This article examines these different permissions types in detail.

### Experience Cloud permissions

This section discusses factors that are important to understand when using [!DNL Platform Launch]. See [Administrative Roles in the Enterprise User Guide](https://helpx.adobe.com/au/enterprise/using/admin-roles.html) for a comprehensive view of [!DNL Experience Cloud] permissions.

#### Organization Administrator

Organization Administrators are often referred to as Org Admins. An Org Admin's main function is to assign permissions to other users. They do this by creating Product Profiles (or groups) that contain a specific set of rights within a specific product and then assigning users, existing or new, to that Product Profile.

Enterprise Org Admins do not inherit any rights in [!DNL Platform Launch]. They must add themselves to a Product Profile that has [!DNL Platform Launch] rights if they want to do anything in [!DNL Platform Launch].

#### Product Administrator

A Product Administrator (or Product Admin) is similar to an Org Admin, but is narrower in scope. A Product Admin only has the permission to modify Product Profiles for a specific [!DNL Adobe] product, rather than all [!DNL Adobe] products the company has access to.

### Platform Launch permissions

Within the [!DNL Experience Cloud], no rights or permissions are assigned to individual users. They are assigned to a Product Profile (see "Experience Cloud Permissions" above). Individual users are then assigned to one or more Product Profiles.

Within a Product Profile, [!DNL Platform Launch] permissions are divided across four dimensions.

1. Platforms
2. Properties
3. Property Rights
4. Company Rights

#### Platforms

Each property has a platform.  There are currently two platforms that you can use in [!DNL Platform Launch]: *Web* and *Mobile*.  You can use this permission type to restrict or grant access to a particular type of property.  This can be useful when the team that manages your mobile apps is different from the one that manages your web sites.

#### Properties

This is a list of all Properties that exist within your company.  You can use this permission type to restrict or grant access to specific existing properties (by name).

#### Property rights

Any properties you create in [!DNL Platform Launch] become available in the Admin Console for you to assign permissions. If a given Product Profile does not have access to Property A1, users who belong to that profile cannot see or modify any settings within Property A1.

Assuming that a user belongs to a profile with access to Property A1, what they can do within Property A1 is determined by the rights they have been granted from this permission group. Users with permissions to Property A1, but no assigned rights, have read-only access.

The permissions available within this group are:

* **Develop:** Grants the ability to create rules and data elements. You can also create libraries and build them in existing development environments. You can submit a library for approval when ready.  Most day-to-day tasks in [!DNL Platform Launch] require this right.
* **Approve:** Grants the ability to take a submitted library and build to the staging environment.  You can also approve a library for publishing once testing has been completed.
* **Publish:** Grants the ability to publish approved libraries to the production environment.
* **Manage Extensions:** Grants the abilities to install new extensions to a property, to modify the extension configuration for an already installed extension, and to delete an extension.  More information on extensions is available [here](../managing-resources/extensions/overview.md). This role typically belongs to IT or Marketing, depending on your organization.
* **Manage Environments:** Grants the ability to create and modify environments. Read more about environments [here](../publishing/environments.md). This role typically belongs to the IT group.

#### Company rights

Company rights apply to permissions that span multiple properties.  There are currently two:

* **Manage Properties:** Grants the ability to create new properties in [!DNL Platform Launch] and to modify the metadata and settings at the property level. You can also delete properties.  Read more about properties [here](companies-and-properties.md). Administrators usually perform this role.
* **Develop Extensions:** Grants the ability to create and modify extension packages that are owned by the company including private releases and requests for public release.

### Total user permissions

An individual user's total permissions are determined by their total membership in different Product Profiles. If a user belongs to multiple Product Profiles, the permissions from each profile are added together rather than multiplied.

For example: Product Profile A grants Henry the Develop right for Property 1. Product Profile B grants Henry the Publish right for Property 2. Henry can Develop in Property 1 and Publish in Property 2, but he cannot publish in Property 1 or Develop in Property 2 because he has not been granted explicit rights to do so.

## Rights scenarios 

Different companies have different needs when creating new Product Profiles. These needs vary based on company size, org structure, number of sites, number of people involved in managing tags, and so on.

Below are a few common scenarios and a recommended starting point as you think about creating Product Profiles and adding users to them.

### One-person show

If you run a small company that has one person in charge of everything, grant this user permission to all properties and assign them all rights listed above.

### Separation of duties

Many people are involved in tagging. You have one set of people (maybe an external consultant) that creates rules and data elements, but you don't want them to have access to the production environment. You want to make sure that nobody deploys to Production except the IT team.

1. Create an account for your consultants and grant them only the develop right.
1. The consultant builds and tests within the confines you set.
1. If the consultant wants a new extension, or is ready to go live, a representative from your organization (with the appropriate rights), performs those actions.

### Enterprise

An enterprise company might have multiple sites divided geographically, with different teams responsible for each geo. Within those teams, different individuals develop and publish.

This is similar to "Separation of duties" above, but organized by geographic areas.

* North America
  * Develop group
  * Publish group
* Europe
  * Develop group
  * Publish group
* ...
  * Develop group
  * Publish group

## Examples

A few examples of the types of roles you might have in your organization, and which permissions you should assign them, could help to clarify this concept.

Here are a few descriptions of different roles that could apply in your organization and a matrix to show what permissions they need to do their job.

* The Manager: Wants to see what's going on, but shouldn't be able to make any changes.
* The Marketer: Can install extensions and setup new tags for existing properties, but cannot publish to the staging or production environments.
* The Mobile App Developer: Is responsible for implementing Adobe and 3rd-party solutions inside a native mobile app.
* The IT Team: Doesn't actually modify any tags, but they have full control over the staging and production environments and what is in them.
* Jack of All Trades: Does everything.

|Role|Properties|Company Rights|Property Rights|
|--- |--- |--- |--- |
|The Manager|Auto-include|||
|The Marketer|Auto-include|Manage Properties|Develop<br>Manage Extensions|
|The Mobile App Developer|Auto-include|Manage Properties|Develop<br>Manage Extensions|
|The IT Team|Auto-include|Approve<br>Publish<br>Manage Environments|
|The Jack of All Trades|Auto-include|Manage Properties|Develop<br>Approve<br>Publish<br>Manage Extensions<br>Manage Environments|
|The Extension Developer|Auto-include|Manage Properties<br>Develop Extensions|Develop|

## Assigning user permissions

The steps below guide you through the process of assigning permissions. You can also view this process [on video](https://www.youtube.com/watch?v=ba28BHX8cwU).

Steps 1-3 below can be bypassed by navigating directly to [Adobe Admin Console](https://adminconsole.adobe.com/enterprise/products). If you belong to more than one organization, select the correct org from the top nav on the right.

### 1. Sign in to Experience Cloud

Sign in to [https://experiencecloud.adobe.com/](https://experiencecloud.adobe.com/) with your [!DNL Adobe] ID, then choose the organization to use within [!DNL Platform Launch] from the [!UICONTROL Navigation] menu.

![](/help/assets/nav-menu.png)

Open the solution picker by selecting  the 9-dots icon from the [!UICONTROL Navigation] menu, then select [!UICONTROL Administration].

![](/help/assets/choose-admin.png)

If you can't see this link, both of the following conditions are true:

* You are not an org admin.
* You are not a product admin for any [!DNL Experience Cloud] products.

In either case, ask an org admin to perform these steps for you, or to make you a product admin for [!DNL Platform Launch] so you can do it yourself.

>[!NOTE]
>
>If you don't know who your org admin is, contact Client Care.

### 2. Open Admin Console

Select **Platform Launch Admin Console**.

![](/help/assets/launch-admin-console-button.png)

Select the **[!DNL Experience Platform Launch] - `Company Name`** card.

![](/help/assets/launch-card.png)

<!-- Scott, update above image. Rebranding. -->

You can also select [!UICONTROL Products] in the top nav, then select **[!DNL Experience Platform Launch] - `Company Name`** from the left nav.

![](/help/assets/products-select-launch.png)

If you do not see a [!DNL Experience Platform Launch] card and or if [!DNL Experience Platform Launch] does not appear in this list, then you are not an Org Admin, but you are a Product Admin for other Experience Cloud products. Because you are not an Administrator for Experience Platform Launch, you need to find an Org Admin who can perform these steps for you or who can make you a Product Admin for [!DNL Platform Launch].

After you select Platform Launch, a list of product profiles displays. Think of these profiles as permission groups. One profile is created for you and is named "[!DNL Platform Launch] - `Company Name`."

![](/help/assets/product-profiles.png)

### 3. Create your product profile

If you are editing an existing product profile, skip this step.

Choose to edit this product profile, or create a new one.

To create a new product profile, select [!UICONTROL New Profile].

Give your new profile a name and a description, configure whether users should receive emails when they are added or removed from this profile, and then select [!UICONTROL Done].

![](/help/assets/profile-new.png)

### 4. Edit your product profile

Select the product profile from the list, then open the [!UICONTROL Permissions] tab. You can assign permissions across two dimensions: Properties and Rights.

![](/help/assets/profile-permissions.png)

To assign properties to this group definition, open the [!UICONTROL Properties] section.

![](/help/assets/profile-properties-select.png)

A list shows your [!DNL Platform Launch] properties.

![](/help/assets/profile-properties.png)

By default, new product configurations automatically include properties. This means that all properties (present and future) are included in the group definition.

If Auto-include is disabled, all currently available properties are listed on the left. You can move properties into this group definition by selecting  [!UICONTROL Add].

![](/help/assets/profile-properties-add.png)

Select [!UICONTROL Save] when finished.

### 5. Assign rights

Assign the rights you want to be part of your group definition. Open the [!UICONTROL Rights] section.

![](/help/assets/profile-rights-select.png)

Rights are not automatically included. You must assign each right to your profile. You can quickly add all rights to this profile by using the [!UICONTROL + Add All] button or you can assign individual rights by using the individual + buttons. For more information on what permissions are associated with each right, see [Rights scenarios](#rights-scenarios). Select [!UICONTROL Save] when finished. If [!UICONTROL Save] is not available, you didn't make any changes and the profile won't give you any rights.

First, assign Property Rights:

![](/help/assets/rights-property.png)

Then, assign Company Rights.

![](/help/assets/rights-company.png)

Some important notes:

* Lack of rights means read-only access.

  If you belong to a product configuration with Auto-include properties and no rights, then you have read-only access to all properties in Platform Launch.

* If you don't at least assign the Manage Properties right, you won't be able to add any properties when you log in.
* A user can belong to multiple groups, but the rights from those groups are not combined into a master permission set. That user still has only the rights explicitly granted by each group.

  For example, if Group 1 gives access to Property A with the Develop right and Group 2 gives access to Property B with the Publish right, Develop and Publish rights are not combined for Property A and Property B. You can only develop on Property A and publish on Property B.

### 6. Assign users to groups

To assign users to be part of your group, open the [!UICONTROL Users] tab, then select [!UICONTROL Add User].

![](/help/assets/profile-user.png)

Select [!UICONTROL ...] for additional options, such as bulk user operations.

>[!NOTE]
>
>Being an Org Admin or a Product Admin does not grant you any rights within the [!DNL Platform Launch] product. You must belong to at least one product profile.

Search for the user you'd like to add to the group. You can search by name or by email address. This auto-populates from existing users in your Org. Once you have found the user you want, select their name.

Once you've added users, they receive an email letting them know that they now have rights to [!DNL Platform Launch]. They can login to [!DNL Platform Launch] at [https://launch.adobe.com](https://launch.adobe.com).

>[!NOTE]
>
>If the user does not exist, you can simply type their entire email address, then provide a first and last name. The new user receives an email, and when they create an [!DNL Adobe] ID from that email invitation, they are linked together with the user account you created for them. If you are assigning permissions for yourself, you won't have this issue.

## Common issues

### Error loading account

When you log in to [!DNL Platform Launch], you receive a message saying "Error Loading Account".

![](/help/assets/profile-error.png)

Resolution: Your user does not belong to any [!DNL Platform Launch] product profiles. See the steps above to create a profile and assign rights to it, and to assign a user to a profile.

### Grayed-out Property button

Once you've logged in, you can't add any properties.

Resolution: Your user account does not belong to a product configuration that has the Manage Properties right. Go back to Step 5 above.
