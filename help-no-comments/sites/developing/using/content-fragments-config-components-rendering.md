---
title: DO NOT PUBLISH Content Fragments Configuring Components for Rendering
seo-title: DO NOT PUBLISH Content Fragments Configuring Components for Rendering
description: null
seo-description: null
page-status-flag: never-activated
uuid: 1985b229-3c59-4477-82ee-b86daa6df18d
discoiquuid: 5f9b30ef-817a-4f7a-b86f-83e4793f08bb
index: y
internal: n
snippet: y
---

# DO NOT PUBLISH Content Fragments Configuring Components for Rendering{#do-not-publish-content-fragments-configuring-components-for-rendering}

There are several advanced services related to the rendering of content fragments. To use these services, the resource types of such components must make themselves known to the content fragments framework.

This is done by an OSGi configuration, as documented on this page.

>[!NOTE]
>
>If you do not need the services described below, you can ignore this configuration.
>
>You can write a component from scratch that uses the Content Fragments API only, with no advanced services. However, in such a case, you will have to develop your component so that it handles the appropriate processing.

## Definition of Advanced Services {#definition-of-advanced-services}

The services that require the registration of a component are:

* Determining dependencies correctly during publication (i.e. ensure that fragments & models can be automatically published with a page if they have changed since last publication).
* Support for content fragments in full text search.
* The management/handling of *in-between content.*
* The management/handling of *mixed media assets.*
* Dispatcher flush for referenced fragments (if a page containing a fragment is re-published).
* Using paragraph-based rendering.

If you need one or more of these features, then (typically) it is easier to use the out-of-the-box functionality, instead of developing it from scratch.

## OSGi Configuration {#osgi-configuration}

The configuration needs to be bound to the OSGi service **Content Fragment Component Configuration**:

`com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl`

For example:

![](assets/CFM-01.png)

The OSGi configuration is:

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody> 
  <tr> 
   <td>Label</td> 
   <td>OSGi Configuration<br /> </td> 
   <td>Description</td> 
  </tr> 
  <tr> 
   <td><strong>Resource type</strong></td> 
   <td><span class="code">dam.cfm.component.resourceType</span></td> 
   <td>The resource type to register; e.g. <span class="code">core/wcm/extension/components/contentfragment/v1/contentfragment</span></td> 
  </tr> 
  <tr> 
   <td><strong>Reference property</strong></td> 
   <td><span class="code">dam.cfm.component.fileReferenceProp</span></td> 
   <td>The name of the property that contains the reference to the fragment; e.g. <span class="code">fragmentPath</span> or <span class="code">fileReference</span></td> 
  </tr> 
  <tr> 
   <td><strong>Element(s) property</strong></td> 
   <td><span class="code">dam.cfm.component.elementsProp</span></td> 
   <td>The name of the property that contains the name(s) of the element(s) to render; e.g.<span class="code">elementName</span></td> 
  </tr> 
  <tr> 
   <td><strong>Variation property</strong><br /> </td> 
   <td><span class="code">dam.cfm.component.variationProp</span></td> 
   <td>The name of the property that contains the name of the variation to render; e.g.<span class="code">variationName</span></td> 
  </tr> 
 </tbody> 
</table>

For some functionality (e.g. to render only a paragraph range) you will have to adhere to some conventions:

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody> 
  <tr> 
   <td>Property Name</td> 
   <td>Description</td> 
  </tr> 
  <tr> 
   <td><span class="code">paragraphRange</span></td> 
   <td><p>A string property that defines the range of paragraphs to be output if in <em>single element render mode</em>.</p> <p>Format:</p> 
    <ul> 
     <li><span class="code">1</span> or <span class="code">1-3</span> or <span class="code">1-3;6;7-8</span> or <span class="code">*-3;5-*</span></li> 
     <li>only evaluated if <span class="code">paragraphScope</span> is set to <span class="code">range</span></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><span class="code">paragraphScope</span></td> 
   <td><p>A string property that defines how paragraphs are to be output if in <em>single element render mode</em>.</p> <p>Values:</p> 
    <ul> 
     <li><span class="code">all</span> : to render all paragraphs</li> 
     <li><span class="code">range</span> : to render the range of paragraphs provided by <span class="code">paragraphRange</span></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><span class="code">paragraphHeadings</span></td> 
   <td>A boolean property that defines if headings (for example, <span class="code">h1</span>, <span class="code">h2</span>, <span class="code">h3</span>) are counted as paragraphs (<span class="code">true</span>) or not (<span class="code">false</span>)</td> 
  </tr> 
 </tbody> 
</table>

>[!CAUTION]
>
>This may change in later 6.5 milestones.

## Example {#example}

As an example, see the following (on an out-of-the-box AEM instance):

```
/apps/core/wcm/config/com.adobe.cq.dam.cfm.impl.component.ComponentConfigImpl-core-comp-v1.config  
```

This contains:

```
dam.cfm.component.resourceType="core/wcm/extension/components/contentfragment/v1/contentfragment"
dam.cfm.component.fileReferenceProp="fragmentPath"
dam.cfm.component.elementsProp="elementName"
dam.cfm.component.variationProp="variationName"
```
