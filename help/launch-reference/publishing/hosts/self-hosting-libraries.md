---
title: Self-Hosting Libraries
description: Learn how to implement self-hosting for your library builds in Adobe Experience Platform Launch.
exl-id: e8dc1a71-9cb0-4a03-b871-97c5c1b34c63
---
# Self-hosting libraries

Everything you do in Adobe Experience Platform Launch has the ultimate goal of producing a set of files to control the behavior of your application at run-time. This set of files is called a [build](../builds.md).

Builds need to be hosted somewhere so client devices can retrieve them at run-time as needed.

Platform Launch can either manage the hosting of these files for you or you can do it yourself.

## Managed by Adobe {#managed-by-adobe}

Adobe is not in the business of web-hosting.  If you choose to have Adobe manage the hosting, your builds are delivered to a third-party content delivery network (CDN) that we have a contract with.

Currently, the primary CDN provider is Akamai. Files hosted on Akamai have a domain of `assets.adobedtm.com`.

### Why use managed hosting?

The primary reason to use managed hosting is convenience. It is easier to create the required host, and you don't have to worry about maintenance.

## Self-hosting

If you don't want Adobe to manage your hosted files, you must host them yourself. To host your files, you need to get the completed builds from Platform Launch and to be responsible for getting the files through your company's release cycle onto company managed servers.

### Why use self-hosting?

There are a number of reasons to choose to host your own build files.

* Some browsers block the assets.adobedtm.com domain based on the privacy settings the end-user has configured
* Self-hosting reduces the required number of DNS lookups
* You require use of HTTP/2
* You have specific headers you need to set for security
* Your cache control requirements differ from the Adobe default settings
* You want more control over the location of edge nodes
* Your organization has security and legal requirements that prevent you from using the Adobe-managed option

### How to self-host

There are two methods you can use to acquire completed builds so that you can self-host.

* Download
* Direct Delivery

#### Download

You can have Platform Launch deliver builds as a packaged .zip file (encryption optional). You can then unzip the package and insert the contents into your release cycle to place them on your own servers.

Use a [Managed by Adobe](self-hosting-libraries.md) host and select the [Archive](../environments.md) option on your environment. The environment provides a download link. Whenever a build is created, you can retrieve it from the environment's download link.

#### Direct Delivery

You can have Platform Launch deliver builds directly to an SFTP server that you created. You take responsibility to get these filed into your release cycle and push them live.

To perform a direct delivery, you should create an [SFTP host](sftp-host.md) and assign that host to your environment. Whenever you build a library in that environment, the files are delivered to your SFTP server.
