---
title: Create an Exchange Listing for an Extension
description: Learn how to add your extension in Adobe Experience Platform to the public catalog.
exl-id: 93e83a62-6089-48e9-b521-82f972b36ac4
---
# Create an exchange listing for an extension

>[!NOTE]
>
>Adobe Experience Platform Launch is being rebranded as a suite of data collection technologies in Experience Platform. These changes will be rolling out across all product documentation in the coming weeks. Please refer to the following [document](../../launch-term-updates.md) for a consolidated reference of the terminology changes.

Adobe Experience Platform data collection has two catalogs for extensions: Private and Public. The Private catalog is only available within your own organization. If you do not plan on making your extension available to the public, you can skip this step and proceed to the document on [uploading and testing your extension](./upload-and-test.md).

To add your extension to the Public catalog, you must create a listing and include the URL to your listing in the extension.json manifest file inside of your Extension Package. Extensions created for public release are required to have a listing in the [Exchange Marketplace](https://experiencecloud.adobeexchange.com/). These listings enable extension developers to post support information, links to additional support or documentation, and to market your extensions to prospective users who may not be aware of your company or the functionality of your extension. In this marketplace, your extension will have a public listing that can be viewed without the user being authenticated to Adobe Experience Platform data collection.

The listing can be created at any time during the development of the extension, but must be completed and published (with the URL included in your extension package) before your extension can be released publicly.

## Create a listing

>[!NOTE]
>
>The following process details the creation of an application listing in the Adobe Exchange program. This is the term used for the various integrations, and extensions in Adobe Experience Platform data collection. 

![Experience Cloud App Manager link location](../images/getting-started/app-mgr-link.png)

1. Sign in to the [Exchange Partner site](https://partners.adobe.com/exchangeprogram/experiencecloud). Once signed in, select the **App Manager** link next to your name.
2. Select the **Create New Application** tab, and then select **Create New App** for a customized solution, or select an applicable template.
3. Provide your listing information. For detailed information on App Manager check out the full [article](https://adobeexchangeec.zendesk.com/hc/en-us/articles/360024197931). Listing information should be very clear about what the extension does and why it is useful. The listing functions as a marketing space for your app. Promote your extension here using clear descriptions, links to landing pages on your site, links to help docs or support email addresses, and so on. Although space in extension views is limited, the Exchange listing provides an opportunity to promote both your extension and your company. The following are suggestions to improve promotion of the extension:
   - **App Icon** – Make sure the icon for the Exchange listing has the appropriate dimensions, 512 x 512 for png or 1:1 aspect ratio for jpg. 
  **Note**: This is a different file format than used in your extension code. The extension itself will contain an svg file as the [icon](../manifest.md).
   - **Featured Image** - Get attention by using an image that can stand alone and will show your brand and highlight your application. The Featured Image is the one shown when someone shares a link to your Exchange listing or posts about it on social media. It therefore needs to be a model representation of your brand.
   - **App Publisher's Logo** - This is your corporate logo, make sure the icon has the appropriate dimensions of 1280 x 720, or 2560 x 1440 (16:9) in png or jpg format.
   - **Configuration Instructions** – Inform customers how to configure your Adobe Experience Platform extension. Make sure they understand any required settings and next steps when your [configuration view](../configuration.md) appears immediately after installing your extension in a property. 
   - **Tags** - On the first page of editing your listing, please be sure to include the word "Launch" in the 'Custom Tags' field. This will make your listing appear in searches for Data Collection tags in the Exchange marketplace:
     ![](../images/getting-started/custom-tags.jpg)
   - **Sandboxes** - Your access to Adobe Solutions is through a Sandbox account where you have access to a fully functioning version of Adobe Experience Platform. These Sandbox accounts are requested as you create your application listing. In the **Connections** section select the specific connections that are applicable for the application you created (your data collection extension), and when you hit **Save**, the sandbox request will be generated if needed.  
4. Submit your listing. The Adobe Exchange team will review your application and provide feedback if updates are required. If you mark the **publish immediately** checkbox when you submit your listing, it will be published immediately upon approval. If you want to publish your application at a later time, leave the checkbox unchecked. When your extension listing is approved, a blue **Publish** button will appear next to it on your app (extension) listings page.

### Create an effective listing

The [App Submission Guideline](https://partners.adobe.com/exchangeprogram/experiencecloud/build/ec-exchange.html) provides detailed information on how to create an engaging listing.

#### After submitting your Exchange listing

Once submitted, the Adobe Exchange team will review the application and will either approve the application, or respond with comments about changes. This process is detailed in the App Submission Guidelines.

If you don't have a login to the Exchange site, make sure that your email is registered for the Exchange program by following the instructions in the [Program Registration Guide](https://partners.adobe.com/content/mcp/us/en/home/reg-guide.html). Each user must associate their email with the partner account for their company. Questions on this process can be directed via email to <ExchangeHelpEC@adobe.com>.

#### Update your Exchange listing after initial approval

When you update your extension, or need to update your Exchange listing, login to the [Partner Portal](https://partners.adobe.com/exchangeprogram/experiencecloud) and select the App Manager button next to your name. Then select your application and follow the flow above that was initially used to create the listing. Once re-submitted, the Adobe Exchange team will review the changes and will either approve the changes, or respond with comments about the changes.
