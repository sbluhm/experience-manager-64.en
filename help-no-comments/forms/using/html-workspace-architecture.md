---
title: AEM Forms Workspace Architecture
seo-title: AEM Forms Workspace Architecture
description: Conceptual information and overview of the architecture of LiveCycle AEM Forms workspace.
seo-description: Conceptual information and overview of the architecture of LiveCycle AEM Forms workspace.
uuid: 238049e5-4bda-4e36-93e3-6149503adbde
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-workspace
discoiquuid: a0492e84-c79f-4b5b-b514-b1b0f65e0ebe
index: y
internal: n
snippet: y
---

# AEM Forms Workspace Architecture{#aem-forms-workspace-architecture}

AEM Forms workspace is a web application hosted on CRX™. When workspace is opened in a browser, a CRX resource is accessed, and the application is rendered as HTML page in the browser.

The application accesses AEM Forms server on REST endpoints to do the following:

* Fetch user tasks, process startpoints, process history, and user information
* Perform action on tasks
* Query tasks in database
* Update user preferences and more

The AEM Forms server accesses AEM Forms database over JDBC. The database persists tasks, processes and their instances, users, and related information.

The AEM Forms workspace is designed into modular JavaScript™ components which can be individually customized and reused in other web applications. The components are based on BackBone which is a JavaScript library that gives structure to web applications. A detailed article describing interaction of components with BackBone is [here](../../forms/using/backbone-interaction.md). The organization of components in the CRX folder structure is discussed in [this](../../forms/using/folder-structure.md) article.

Packages delivered for AEM Forms workspace:

* `adobe-lc-workspace-pkg-<version>.zip`: It is CRX package, that is, it can be deployed in CRX using the Package Manager.
* `adobe-lc-workspace-<version>-src.zip`: It is an archive that contains complete code of AEM Forms workspace and scripts to create the deploy packages--Ship, Debug, and Dev packages.

[**Contact Support**](https://www.adobe.com/account/sign-in.supportportal.html)