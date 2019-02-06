---
title: Configure adaptive forms cache
seo-title: Configure adaptive forms cache
description: The adaptive forms cache is designed specifically for adaptive forms and documents. It caches adaptive forms and adaptive documents with the objective of reducing the time required to render an adaptive form or document on the client. 
seo-description: The adaptive forms cache is designed specifically for adaptive forms and documents. It caches adaptive forms and adaptive documents with the objective of reducing the time required to render an adaptive form or document on the client. 
uuid: c8949936-35dc-4c58-b293-50cf2f8ff049
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: a32e7eee-2476-40e2-a96d-636c1180f084
index: y
internal: n
snippet: y
---

# Configure adaptive forms cache{#configure-adaptive-forms-cache}

A cache is a mechanism to shorten data access times, reduce latency, and improve input/output (I/O) speeds. Adaptive forms cache stores only HTML content and JSON structure of an adaptive form without saving any pre-filled data. It helps in reducing the time required to render an adaptive form or document on the client. It is designed specifically for adaptive forms and also supports adaptive documents.

>[!NOTE]
>
>When using the adaptive forms cache, use the AEM Dispatcher to cache client libraries (CSS and JavaScript) of an adaptive form or document.

>[!NOTE]
>
>While developing custom components, on the server used for development, keep the adaptive forms cache disabled.

### Configure the cache {#configure-the-cache}

Perform the following steps to configure the adaptive forms cache:

1. Go to AEM web console configuration manager at http://[server]:[port]/system/console/configMgr.
1. Click **Adaptive Form and Interactive Communication Web Channel Configuration** to edit its configuration values.
1. In the edit configuration values dialog, specify the maximum number of forms or documents an instance of the AEM Forms server can cache in the **Number of Adaptive Forms** field. The default value is 100.

   >[!NOTE]
   >
   >To disable the cache, set the value in the Number of Adaptive Forms field to **0**. The cache is reset and all forms and documents are removed from the cache when you disable or change the cache configuration.

   ![Configuration dialog for adaptive forms HTML cache](assets/cache-configuration-edit.png)

1. Click **Save** to save the configuration.
