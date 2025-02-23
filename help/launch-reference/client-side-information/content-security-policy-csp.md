---
title: Content Security Policy (CSP) Support
description: Learn how to deal with Content Security Policy (CSP) restrictions when integrating Adobe Experience Platform Launch into your website.
exl-id: 362d9945-6b71-48a2-97c4-af030544aaa2
---
# Content Security Policy (CSP) support

A Content Security Policy (CSP) is a security feature that helps prevent cross-site scripting attacks (XSS). This happens when the browser is tricked into running malicious content that appears to come from a trusted source, but is really coming from somewhere else. CSPs allow the browser (on behalf of the user) to verify that the script is actually coming from a trusted source.

CSPs are implemented by adding a `Content-Security-Policy` HTTP header to your server responses, or by adding a configured `<meta>` element in the `<head>` section of your HTML files.

>[!NOTE]
>
> For more detailed information on CSP, refer to the [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP).

As a tag management system, Adobe Experience Platform Launch is designed to dynamically load scripts on your website. A default CSP blocks these dynamically loaded scripts due to potential security problems. This document provides guidance on how to configure your CSP to allow dynamically loaded scripts from [!DNL Platform Launch].

If you want Adobe Experience Platform Launch to work with your CSP, there are two main challenges to overcome:

* **The source for your Platform Launch library must be trusted.** If this condition is not met, the Platform Launch library and other required JavaScript files are blocked by the browser and won't load on the page.
* **Inline scripts must be allowed.** If this condition is not met, Custom Code rule actions are blocked on the page and won't execute properly.

If you want to use Platform Launch _and_ have a CSP in place, you have to fix both of these problems without incorrectly marking other scripts as safe. Increasing security comes at the price of increasing the amount of work on your part.

If you want to use [!DNL Platform Launch] and have a CSP in place, you have to address both of these issues without incorrectly marking other scripts as safe. The rest of this document provides guidance on how to achieve this.

## Add [!DNL Platform Launch] as a trusted source

When using a CSP, you must include any trusted domains within the value of the `Content-Security-Policy` header. The value you must provide for [!DNL Platform Launch] will vary depending on the type of hosting you are using.

### Self-hosting

If you are [self-hosting](../publishing/hosts/self-hosting-libraries.md) your library, then the source for your build is probably your own domain. You can specify that the host domain is a safe source by using the following configuration:

**HTTP header**

```http
Content-Security-Policy: script-src 'self'
```

**HTML `<meta>` tag**

```html
<meta http-equiv="Content-Security-Policy" content="script-src 'self'">
```

### Adobe-managed hosting

If you are using an [Adobe-managed host](../publishing/hosts/managed-by-adobe-host.md), then your build is maintained on `assets.adobedtm.com`. You should specify `self` as a safe domain so you don't break any scripts that you are already loading, but you also need `assets.adobedtm.com` to be listed as safe or your Platform Launch library won't load on the page. In this case, you should use the following configuration:

**HTTP header**

```http
Content-Security-Policy: script-src 'self' assets.adobedtm.com
```

**HTML `<meta>` tag**


There is a very important prerequisite: You must load the Platform Launch library [asynchronously](https://docs.adobe.com/content/help/en/launch/using/reference/client-side-info/asynchronous-deployment.html). This does not work with a synchronous load of the Platform Launch library (which results in console errors and rules not executing properly).

```html
<meta http-equiv="Content-Security-Policy" content="script-src 'self' assets.adobedtm.com">
```

You should specify `self` as a safe domain so that any scripts that you are already loading continue to work, but you also need `assets.adobedtm.com` to be listed as safe or your library build won't load on the page.

## Inline scripts

CSP disallows inline scripts by default, and therefore must be manually configured to allow them. You have two options to allow inline scripts:

* [Allow by nonce](#nonce) (good security)
* [Allow all inline scripts](#unsafe-inline) (least secure)

>[!NOTE]
>
>The CSP specification has details for a third option using hashes, but this approach is not feasible to use with tag management systems like [!DNL Platform Launch]. For more information on the limitations of using hashes in [!DNL Platform Launch], see the [Subresource Integrity (SRI) guide](./sri.md).

### Allow by nonce {#nonce}

This method involves generating a cryptographic nonce and adding it to your CSP and every inline script on your site. When the browser receives an instruction to load an inline script with a nonce on it, the browser compares the nonce value to what is contained within the CSP header. If it matches, the script is loaded. This nonce should be changed with each new page load.

>[!IMPORTANT]
>
>In order to use this method, you must load the build asynchronously. This does not work when loading the build synchronously, which results in console errors and rules not executing properly. See the guide on [asynchronous deployment](./asynchronous-deployment.md) for more information.

The examples below show how you can add your nonce to the CSP configuration for an Adobe-managed host. If you are using self-hosting, you can exclude `assets.adobedtm.com`.

**HTTP header**

```http
Content-Security-Policy: script-src 'self' assets.adobedtm.com 'nonce-2726c7f26c'
```

**HTML `<meta>` tag**

```html
<meta http-equiv="Content-Security-Policy" content="script-src 'self' assets.adobedtm.com 'nonce-2726c7f26c'">
```

Once you configure your header or HTML tag, must then tell [!DNL Platform Launch] where to find the nonce when loading an inline script. For [!DNL Platform Launch] to use the nonce when loading the script, you must:

1. Create a data element that references where the nonce is located within your data layer.
2. Configure the Core Extension and specify which data element you used.
3. Publish your data element and Core Extension changes.

>[!NOTE]
>
>The above process only handles loading your custom code, not what that custom code does. If an inline script contains custom code that is not compliant with your CSP, the CSP takes precedence. For example, if you use custom code to load an inline script by appending it to the DOM, [!DNL Platform Launch] cannot add the nonce correctly, so that particular custom code action will not work as expected.

### Allow all inline scripts {#unsafe-inline}

If using nonces does not work for you, you can configure your CSP to allow all inline scripts. This is the least secure option, but is also easier to implement and maintain.

The examples below show how can allow all inline scripts in the CSP header.

#### Self-hosting

Use the following configurations if you are using self-hosting:

**HTTP header**

```http
Content-Security-Policy: script-src 'self' 'unsafe-inline'
```

**HTML `<meta>` tag**

```html
<meta http-equiv="Content-Security-Policy" content="script-src 'self' 'unsafe-inline'">
```

#### Adobe-managed hosting

Use the following configurations if you are using Adobe-managed hosting:

**HTTP header**

```http
Content-Security-Policy: script-src 'self' assets.adobedtm.com 'unsafe-inline'
```

**HTML `<meta>` tag**

```html
<meta http-equiv="Content-Security-Policy" content="script-src 'self' assets.adobedtm.com 'unsafe-inline'">
```

## Next steps

By reading this document, you should now understand how to configure your CSP header to accept the [!DNL Platform Launch] library file and inline scripts.

As an additional security measure, you may also opt to use Subresource Integrity (SRI) to validate fetched library builds. However, this feature has some major limitations when used with tag management systems like [!DNL Platform Launch]. See the guide on [SRI compatibility in [!DNL Platform Launch]](./sri.md) for more information.
