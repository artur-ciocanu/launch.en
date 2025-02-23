---
title: Release Notes for the Adobe Target v2 Extension
description: The latest release notes for the Adobe Target v2 extension in Adobe Experience Platform Launch.
exl-id: b18889e8-a2a2-44bf-acb6-7693b4d1bbca
---
# Adobe Target v2 Extension release notes

## March 25, 2021

### Adobe Target v2 Extension 0.13.7

- Fixed an issue with `targetPageParams` being included in mbox requests. `targetPageParams` should only be included in `pageLoad` requests.
- Fixed an issue with document and window global objects in the Adobe Experience Platform Launch extension by replacing the Platform Launch global object dependencies with direct references to them. 
- Updated at.js to 2.4.1.

## January 25, 2021

### Adobe Target v2 Extension 0.13.6

- Adds support for unified profile/platform ID to delivery API customerIds
- Fixes invalid style tag injection
- Updated at.s to 2.4.0
- Resolved issue where undefined params can result in bad delivery requests

## November 25, 2020

### Adobe Target v2 Extension 0.13.4

- Fixed a bug where mbox parameters were not displaying in the UI
- Branding updates
- Updated the at.js version to 2.3.3

## July 24, 2020

### Adobe Target v2 Extension 0.13.3

- Fixed a bug that caused QA mode links not to work for inactive activities
- Fixed a bug when the extension fails if a script or code adds `default` property to the `window` or `document`

## June 15, 2020

### Adobe Target v2 Extension 0.13.2

- Fixed an issue when using CNAME and edge override, where at.js 1.x might incorrectly create the server domain, resulting in the Target request failing
- Fixed an issue where, when using Target extension v2 for Adobe Experience Platform Launch and Adobe Analytics extension, Target delayed the Analytics sendBeacon call
- Improved the `deviceIdLifetime` setting by making it overridable via `targetGlobalSettings`

## March 25, 2020

### Adobe Target v2 Extension 0.13.0

- Updated at.js to v2.3.
- Added Target Global Mbox support in adobe.target.getOffer API
- Fixed an issue where params and page load params were not processed correctly

## October 10, 2019

### Adobe Target v2 Extension 0.12.0

- Updated at.js to v2.2.
- Improved performance for integrations between Experience Cloud ID library (ECID) v4.4 and at.js 2.2.
- Previously, the ECID library made two blocking calls before at.js could fetch experiences. This has been reduced to a single call, which significantly improves performance.

>[!NOTE]
>Please upgrade your ECID extension for Platform Launch to v4.4.1 to take advantage of this performance enhancement.

## July 31, 2019

### Adobe Target v2 Extension 0.11.1

- Updated extension version to use at.js 2.1.1
- Added a fix for handling parameters

## June 3, 2019

### Adobe Target v2 Extension 0.11.0

- New Platform Launch extension to support at.js 2.1
