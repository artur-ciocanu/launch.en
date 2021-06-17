---
title: SFTP Hosts
description: Learn how to configure tags in Adobe Experience Platform to deliver library builds to a secured, self-hosted SFTP server.
exl-id: 8908e22c-346e-454d-b612-b2264b119a50
---
# SFTP hosts

>[!NOTE]
>
>Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../../../launch-term-updates.md) for a consolidated reference of the terminology changes.

If you do not want to have Adobe manage your hosted libraries, your other option is to have Adobe Experience Platform deliver builds to a secured SFTP server that you host.

Platform connects to your SFTP site using an encrypted key. There are a few steps to set this up correctly:

1. You must have a public/private key pair installed on your SFTP server. You can generate these keys on your server or generate them somewhere else and install them on your server. See [here](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/#generating-a-new-ssh-key)for an example of how to generate keys.
2. You must encrypt the private key with tags' public GPG key so that you can provide your private key to tags during the SFTP host creation process. See [Encrypting Values](https://developer.adobelaunch.com/api/guides/encrypting_values/) in the Reactor API documentation for instructions and tags' public GPG keys. Unless you know you need a different one, use the Production Environment's GPG key. Finally, you can encrypt your private key from any machine, so you do not need to install GPG on your server to complete this step.
3. You might need to approve the tags' IP addresses with your company firewall to allow Platform to reach your SFTP server and connect to it. Those IP Addresses are:
   * `184.72.239.68`
   * `23.20.85.113`
   * `54.226.193.184`

>[!NOTE]
>
>The structure of tag builds in Adobe Experience Platform has changed over time. They use symbolic links (symlinks) internally to maintain backward compatibility so that previous embed codes will continue to work with the latest build structure. Your SFTP server must support the usage of symlinks in order to serve as a valid destination for tag builds.

There is a full guide [in a Medium article](https://medium.com/launch-by-adobe/configuring-an-sftp-server-for-use-with-adobe-launch-bc626027e5a6) on how to set up SFTP servers for a tag build delivery.

## Create an SFTP host

1. Open the [!UICONTROL Hosts] tab.
1. Create the new Host.
1. Name your host.
1. Select **[!UICONTROL SFTP]** as the host type.
1. Enter the host, path, port, username, and encrypted private key.

   The port must be one of the following:

   * 21
   * 22
   * 80
   * 200-299
   * 443
   * 2000-2999
   * 4343
   * 8080
   * 8888
   
   >[!NOTE]
   >
   >As a security best practice, Adobe limits the number of ports that can be used for outgoing traffic. The selected ports are commonly allowed through corporate firewalls, plus they include some ranges for flexibility.

1. Select **[!UICONTROL Save]**.

When you select **[!UICONTROL Save]**, tags tests whether it is able to connect and deliver files to your SFTP server. It creates a folder, writes a file within that folder, checks to make sure the file is there, then cleans up after itself. If the user account on your SFTP server (the one attached to the secure certificate you provided to Platform) does not have the necessary permissions to perform this action, then the Host goes into a "Failed" status.
