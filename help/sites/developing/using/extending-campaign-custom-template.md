---
title: Creating Custom AEM Page Template with Adobe Campaign Form Components
seo-title: Creating Custom AEM Page Template with Adobe Campaign Form Components
description: Build a custom page template that uses Adobe Campaign Form components
seo-description: Build a custom page template that uses Adobe Campaign Form components
uuid: 0a2f7601-020a-4952-abca-48ac6dfd34e2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 52c537fb-a357-4a10-8d84-3883d3aaf61c
---

# Creating Custom AEM Page Template with Adobe Campaign Form Components{#creating-custom-aem-page-template-with-adobe-campaign-form-components}

This page explains how to build a custom page template that uses [Adobe Campaign Form](../../../sites/authoring/using/adobe-campaign-components.md) components by examining how the Geometrixx-outdoors template ( `/apps/geometrixx-outdoors/components/page_campaign_profile`) is implemented, and points you to important information you may need when creating your own custom template.

>[!NOTE]
>
>[Email and form samples are only available in Geometrixx](../../../sites/developing/using/we-retail.md#weretail). Please download sample Geometrixx content from Package Share.

To create a custom AEM page template using Adobe Campaign Form components, make sure you have the following:

1. Make sure the page-component inherits from `mcm/campaign/components/profile`.

   This is required for the servlets to get and save info

    * `com.day.cq.mcm.campaign.servlets.TemplateListServlet`
    * `com.day.cq.mcm.campaign.servlets.SaveProfileServlet`

   ![](assets/chlimage_1-212.png)

1. When you look at the clientcontext settings ( `/etc/designs/geometrixx-outdoors/jcr:content/page_campaign_profile`) you see the following settings:

    * ClientContext points to `/etc/clientcontext/campaign`
    * There is also an extra *config* node.

   ![](assets/chlimage_1-213.png)

1. In **head.jsp**, you see the following lines that use the **clientcontext-config** and the **cloudservice-hook**:

   ```
   <cq:include path="config" resourceType="cq/personalization/components/clientcontext_optimized/config"/>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub"/>
   <cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
   ```

1. In **body.jsp**, the cloud services are loaded at the bottom of the page:

   ```
   <cq:include path="cloudservices" resourceType="cq/cloudserviceconfigs/components/servicecomponents"/>
   ```

1. To be able to select an Adobe Campaign template the page-properties are extended with the **Campaign** tab:

   ![](assets/chlimage_1-214.png)

1. **Template settings**.

   In the template ( `/apps/geometrixx-outdoors/templates/campaign_profile/jcr:content`) you see the following default values:

   | **acMapping** |mapRecipient (for Adobe Campaign 6.1), profile (for Adobe Campaign Standard) |
   |---|---|
   | **acTemplateId** |mail |

   ![](assets/chlimage_1-215.png)
