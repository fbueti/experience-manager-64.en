---
title: Enabling CRXDE Lite in AEM
seo-title: Enabling CRXDE Lite in AEM
description: Learn how to enable CRXDE Lite in AEM.
seo-description: Learn how to enable CRXDE Lite in AEM.
uuid: d7a3db67-6384-463b-9aa9-f08ecc6c99c6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 72df3ece-badf-466b-8f9a-0ec985d87741
exl-id: 3d8dc987-2ff9-4f71-bc07-48018caa3af4
---
# Enabling CRXDE Lite in AEM{#enabling-crxde-lite-in-aem}

In order to ensure that AEM installations are as secure as possible, the security checklist recommends [disabling WebDAV](/help/sites-administering/security-checklist.md#disable-webdav) in production environments.

However, CRXDE Lite depends on the `org.apache.sling.jcr.davex` bundle to function properly, so disabling WebDAV will effectively disable CRXDE Lite as well.

When this happens, browsing to `https://serveraddress:4502/crx/de/index.jsp` will display an empty root node, and all HTTP requests to CRXDE Lite resources will fail:

```xml
404 Resource at '/crx/server/crx.default/jcr:root/.1.json' not found: No resource found
```

While this recommendation is intended to reduce attack surfaces as much as possible, system administrators might sometimes need access to CRXDE Lite in order to browse content or debug issues on production instances.

If disabled, you can turn CRXDE Lite on by following the below procedure:

1. Go to the OSGi Components console at `http://localhost:4502/system/console/components`
1. Search for the following component:

    * `org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`

1. Click the wrench icon next to it in order to see its configuration options:

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. Create the following configuration:

    * **Root path:** `/crx/server`
    * Tick the box under **Use absolute URIs**.

1. When finished using CRXDE Lite, make sure you disable WebDAV again.

You can also enable CRXDE Lite via cURL, by running this command:

```shell
curl -u admin:admin -F "jcr:primaryType=sling:OsgiConfig" -F "alias=/crx/server" -F "dav.create-absolute-uri=true" -F "dav.create-absolute-uri@TypeHint=Boolean" http://localhost:4502/apps/system/config/org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet
```

## Other Resources {#other-resources}

For more information on AEM 6 security features, see the following pages:

* [The AEM Security Checklist](/help/sites-administering/security-checklist.md)
* [Running AEM in Production Ready Mode](/help/sites-administering/production-ready.md)
